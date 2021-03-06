# Linux内核高端内存

## Linux内核地址空间划分

通常**32位Linux内核**地址空间划分0~3G为用户空间，3~4G为内核空间。注意这里是32位内核地址空间划分，64位内核地址空间划分是不同的。

![](http://oklbfi1yj.bkt.clouddn.com/Linux%E5%86%85%E6%A0%B8%E9%AB%98%E7%AB%AF%E5%86%85%E5%AD%98/1.png)

## Linux内核高端内存的由来

当内核模块代码或线程访问内存时，代码中的内存地址都为逻辑地址，而对应到真正的物理内存地址，需要地址**一对一**的映射。

假如辑地址0xc0000003对应的物理地址为0x3，0xc0000004对应的物理地址为0x4，… …，逻辑地址与物理地址对应的关系为：物理地址 = 逻辑地址 – 0xC0000000

| **逻辑地址**       | **物理内存地址**        |
| -------------- | ----------------- |
| 0xc0000000     | 0x0               |
| 0xc0000001     | 0x1               |
| 0xc0000002     | 0x2               |
| 0xc0000003     | 0x3               |
| …              | …                 |
| 0xe0000000     | 0x20000000        |
| …              | …                 |
| **0xffffffff** | **0x40000000 ??** |

假设按照上述简单的地址映射关系，那么内核逻辑地址空间访问为0xc0000000 ~ 0xffffffff，那么对应的物理内存范围就为0x0 ~ 0x40000000，即只能访问1G物理内存。若机器中安装8G物理内存，那么内核就只能访问前1G物理内存，后面7G物理内存将会无法访问，因为内核的地址空间已经全部映射到物理内存地址范围0x0 ~ 0x40000000。即使安装了8G物理内存，那么物理地址为0x40000001的内存，内核该怎么去访问呢？代码中必须要有更多的内存逻辑地址，而逻辑地址0xc0000000 ~ 0xffffffff的地址空间已经被用完了，所以无法访问物理地址0x40000000以后的内存。

显然不能将内核地址空间0xc0000000 ~ 0xfffffff全部用来简单的地址映射（也就是不能简单的把虚拟地址和物理地址做一一映射，否则，会浪费物理内存空间）。因此x86架构中将内核地址空间划分三部分：ZONE_DMA、ZONE_NORMAL和ZONE_HIGHMEM。ZONE_HIGHMEM即为高端内存，这就是内存高端内存概念的由来。

在x86结构中，三种类型的区域如下：

**ZONE_DMA  **      内存开始的16MB

**ZONE_NORMAL  **     16MB~896MB

**ZONE_HIGHMEM**       896MB ~ 结束

![](http://oklbfi1yj.bkt.clouddn.com/Linux%E5%86%85%E6%A0%B8%E9%AB%98%E7%AB%AF%E5%86%85%E5%AD%98/2.png)

## Linux内核高端内存的理解

前面我们解释了高端内存的由来。 Linux将内核地址空间划分为三部分ZONE_DMA、ZONE_NORMAL和ZONE_HIGHMEM，高端内存HIGH_MEM地址空间范围为0xF8000000 ~ 0xFFFFFFFF（896MB～1024MB）。那么如内核是**如何借助128MB高端内存地址空间是如何实现访问可以所有物理内存**？

当内核想访问高于896MB物理地址内存时，从0xF8000000 ~ 0xFFFFFFFF地址空间范围内找一段相应大小空闲的逻辑地址空间，借用一会。借用这段逻辑地址空间，建立映射到想访问的那段物理内存（即填充内核PTE页面表），**临时用一会，用完后归还**。这样别人也可以借用这段地址空间访问其他物理内存，实现了使用有限的地址空间，访问所有所有物理内存。如下图：

![](http://oklbfi1yj.bkt.clouddn.com/Linux%E5%86%85%E6%A0%B8%E9%AB%98%E7%AB%AF%E5%86%85%E5%AD%98/3.png)

例如内核想访问2G开始的一段大小为1MB的物理内存，即物理地址范围为0x80000000 ~ 0x800FFFFF。访问之前先找到一段1MB大小的空闲地址空间，假设找到的空闲地址空间为0xF8700000 ~ 0xF87FFFFF，用这1MB的逻辑地址空间映射到物理地址空间0x80000000 ~ 0x800FFFFF的内存。映射关系如下：

| **逻辑地址**   | **物理内存地址** |
| ---------- | ---------- |
| 0xF8700000 | 0x80000000 |
| 0xF8700001 | 0x80000001 |
| 0xF8700002 | 0x80000002 |
| …          | …          |
| 0xF87FFFFF | 0x800FFFFF |

**当内核访问完0x80000000 ~ 0x800FFFFF物理内存后，就将0xF8700000 ~ 0xF87FFFFF内核线性空间释放。这样其他进程或代码也可以使用0xF8700000 ~ 0xF87FFFFF这段地址访问其他物理内存**。

从上面的描述，我们可以知道**高端内存的最基本思想**：借一段地址空间，建立临时地址映射，用完后释放，达到这段地址空间可以循环使用，访问所有物理内存。

看到这里，不禁有人会问：万一有内核进程或模块一直占用某段逻辑地址空间不释放，怎么办？若真的出现的这种情况，则内核的高端内存地址空间越来越紧张，若都被占用不释放，则不能建立其他映射到物理内存，其他物理内存都无法被访问了。

## Linux内核高端内存的划分

内核将高端内存划分为3部分：VMALLOC_START~VMALLOC_END、KMAP_BASE~FIXADDR_START和FIXADDR_START~4G。

![](http://oklbfi1yj.bkt.clouddn.com/Linux%E5%86%85%E6%A0%B8%E9%AB%98%E7%AB%AF%E5%86%85%E5%AD%98/4.png)

对于高端内存，可以通过 alloc_page() 或者其它函数获得对应的 page，但是要想访问实际物理内存，还得把 page 转为线性地址才行（为什么？想想 MMU 是如何访问物理内存的），也就是说，我们**需要为高端内存对应的 page 找一个线性空间，这个过程称为高端内存映射**。

## 常见问题

### 用户空间（进程）是否有高端内存概念？

用户进程没有高端内存概念。只有在内核空间才存在高端内存。**用户进程最多只可以访问3G物理内存，而内核进程可以访问所有物理内存**。

### 64位内核中有高端内存吗？

目前现实中，64位Linux内核不存在高端内存，因为64位内核可以支持超过512GB内存。**若机器安装的物理内存超过内核地址空间范围，就会存在高端内存**。

### 用户进程能访问多少物理内存？内核代码能访问多少物理内存？

32位系统用户进程最大可以访问3GB，内核代码可以访问所有物理内存。

64位系统用户进程最大可以访问超过512GB，内核代码可以访问所有物理内存。

### 为什么不把所有的地址空间都分配给内核？

若把所有地址空间都给内存，那么用户进程怎么使用内存？怎么保证内核使用内存和用户进程不起冲突？



