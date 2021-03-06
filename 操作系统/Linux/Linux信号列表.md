# Linux信号列表

## 1、SIGINT

程序终止(interrupt)信号, 在用户键入INTR字符(通常是Ctrl-C)时发出，用于通知前台进程组终止进程。

## 2、SIGBUS

非法地址, 包括内存地址对齐(alignment)出错。比如访问一个四个字长的整数, 但其地址不是4的倍数。它与SIGSEGV的区别在于后者是由于对合法存储地址的非法访问触发的(如访问不属于自己存储空间或只读存储空间)。

## 3、SIGKILL

用来**立即结束**程序的运行.。本信号**不能被阻塞、处理和忽略**。如果管理员发现某个进程终止不了，可尝试发送这个信号。

## 4、SIGSEGV

试图访问未分配给自己的内存，或试图往没有写权限的内存地址写数据。

## 5、SIGALRM

时钟定时信号，计算的是实际的时间或时钟时间。alarm函数使用该信号。

## 6、SIGCHLD

子进程结束时，父进程会收到这个信号。

如果**父进程没有处理这个信号，也没有等待(wait)子进程，子进程虽然终止，但是还会在内核进程表中占有表项，这时的子进程称为僵尸进程**。这种情况我们应该避免(父进程要么忽略SIGCHILD信号，要么捕捉它，或者wait它派生的子进程，或者父进程先终止，这时子进程的终止自动由init进程来接管)。





