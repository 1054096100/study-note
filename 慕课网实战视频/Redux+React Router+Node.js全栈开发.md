# Redux+React Router+Node.js全栈开发

## 第1章：介绍课程目标和学习内容

### React官方脚手架

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/1.png)

安装create-react-app：

```shell
npm install -g create-react-app
```

创建react项目：

```shell
create-react-app imooc
```

脚手架生成的目录：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/2.png)

其中，在文件`src/App.js`里面有一个App class。一个class就是一个组件。

其中，`package.json`中的内容：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/4.png)

**scripts表示npm可以执行的命令**。例如`npm start`。

所有目录的存放的东西：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/3.png)

启动项目：

```shell
npm start
```

### 脚手架命令

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/5.png)

其中，npm install用来安装第三方库，`--save`代表把项目的依赖关系保存到`package.json`中。

例如执行：

```shell
npm install redux --save
```

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/6.png)

会发现，依赖中多了一个redux。

然后，我们在`src/App.js`中导入这个`redux`：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/7.png)

然后，执行：

```shell
npm run eject
```

将会多出目录：scripts、config。并且，`package.json`中的依赖多了很多其他东西。

## 第2章：知识储备

### 2-1: 环境准备

使用react官方推荐的脚手架create-react-app

- 安装nodejs
- npm install -g create-react-app安装脚手架
- create-react-app mushroom创建react项目

### 2-2：ES6常用语法

#### ES6是什么？

它是新的Javascript语法标准

- 2015年6月正式发布
- 使用babel语法转换器,支持低端浏览器
- 流行的库基本都基于ES6构建, React默认使用ES6新语法开发

#### ES6语法概览

- 块级作用域、字符串、函数
- 对象扩展、解构
- 类、模块化等

##### let和const

- 定义变量使用let替代var

  在块作用域中定义的变量，是不可以在块的外面获得

- Const定义不可修改的变量

- 作用域和{}

##### 字符串出纳

- 使用反引号，直接写变量

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/8.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/9.png)

  效果是一样的。

- 多行字符串

- 告别+拼接字符串

##### 函数扩展

- 参数默认值

- 箭头函数

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/10.png)

  其中，hello1是函数名，name是传递给函数hello1的参数。

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/11.png)

  可以看出，结果是一样的。

  使用箭头函数的好处之一是可以简写函数：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/12.png)

  如果函数体只有一条return语句的话，大括号是可以简写的：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/13.png)

  其中，x是函数double的参数，x*2时函数double的返回值。

  所以，结果如下：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/14.png)

  第二个好处是保持this作用域。

- 展开运算符

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/15.png)

  也就是说，可以把数组arr展开，然后传给name1和name2。

  如果我们想要在浏览器中查看结果，那么需要在`index.js`文件中导入这个`es.js`文件。

  (我们写好的组件，如果需要使用，也需要在`index.js`这个文件中引入)

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/16.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/17.png)

##### 对象扩展

- Object.keys、values、 entries

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/18.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/19.png)

  也就是说，**把对象转换为了数组**。

- 对象方法简写,计算属性

- 展开运算符(不是ES6标准,但是babel也支持)

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/20.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/21.png)

  可以看出，obj1和obj2现在合为一个对象了。并且后面的hht把前面的imooc给覆盖了。

##### 结构赋值

函数也可以多返回值了

- 数组解构

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/22.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/23.png)

- 对象解构

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/24.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/25.png)

##### 类

提供class的语法糖

- 是prototype的语法糖

- Extends继承

- Constructor构造函数

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/26.png)

  结果：

  ![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/27.png)

##### 新的数据结构

- Set,元素不可重合
- Map
- Symbol

##### 模块化

ES6中自带了模块化机制,告别seajs和require.js

- Import, import{}
- Export、Export default
- Node现在还不支持,还需要用require来加载文件

例如，我在`module1.js`文件中定义了一个变量`name`：

我们可以通过**export**来把它暴露出来，

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/28.png)

我需要在另一个文件中使用变量`name`，则可以使用**import**：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/29.png)

同样的，也可以把一个函数暴露出去：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/30.png)

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/31.png)

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/32.png)

#### 常见代码片段

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/33.png)

### 2-3：Express + mongodb

#### Express+mongodb开发web后台接口

- Express开发web接口
- 非关系型数据库mongodb
- 使用nodejs的mongoose模块链接和操作mongodb

#### Express

基于nodejs , 快速、开放、极简的web开发框架。

安装：

```shell
npm install express --save
```

此时，我们的package.json文件中就有了express这个依赖。

安装完express之后，我们创建一个server文件夹来存放服务端的代码：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/34.png)

然后，我们在server.js文件中写如下代码：

```js
// 因为nodejs目前还没有支持import，所以使用require
const express = require('express');

// 新建app
const app = express();

app.listen(9093, function() {
	console.log('Node app start at port 9093');
});

app.get('/', function(req, res) {
	res.send('<h1> Hello world</h1>');
});
```

然后，我们进入server目录，执行命令：

```shell
node server.js
```

得到结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/35.png)

打印了这条信息，说明服务器正在监听9093端口。

然后，我们通过浏览器访问这个端口：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/36.png)

得到了服务器发给客户端的响应信息。说明，我们的express已经执行起来了。

当然，一般不会直接发送HTML文件，而是返回json数据：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/37.png)

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/38.png)

##### 其他的特性

- app.get、app.post分别开发get和post接口
- app.use使用模块
- res.send、res.json、res.sendfile响应不同的内容

#### nodemon

注意，每次修改了服务端代码之后，需要重启服务器。一般笨的方法就是`Ctrl + c`，然后再执行`node server.js`。除此之外，还可以安装`nodemon`这个工具来帮助我们：

```shell
npm install -g nodemon
```

然后，我们启动服务器就不是使用：

```shell
node server.js
```

，而是使用：

```shell
nodemon server.js
```

#### mongodb + mongoose

Mongodb是非关系型数据库，mongoose是操作mongodb的库。

##### 安装

安装mongodb：

```shell
brew install mongodb
```

如果需要在后台跑mongodb，可以执行：

```shell
brew services start mongodb
```

mongodb默认监听的端口是：27017。

如果不需要在后台执行mongod，可以执行：

```shell
mongod --config /usr/local/etc/mongod.conf
```

安装mongoose：

在项目的根目录下执行命令：

```shell
npm install mongoose --save
```

通过mongoose操作mongodb ,存储的就是json ,相对mysq|来说,要易用很多。

##### mongoose使用

- Connect连接数据库

  ```js
  // 因为nodejs目前还没有支持import，所以使用require
  const mongoose = require('mongoose');
  
  // 连接mongobd
  const DB_URL = 'mongodb://localhost:27017';
  mongoose.connect(DB_URL);
  // 下面的可以不需要（加上这个的原因是方便判断是否连接上了mongodb）
  mongoose.connection.on('connected', function() {
  	console.log('connect mongodb success');
  });
  ```

- 定义文档模型, Schema和model新建模型

  可以把文档模型理解为MySQL中的表。mongo里有文档、字段的概念。

  ```js
  // 类似于mysql中的表，mongo里有文档、字段的概念
  const User = mongoose.model('user', new mongoose.Schema({
  	username: {type: String, require: true},
  	age: {type: Number, require: true}
  }));
  ```

  model后面的`'user'`指的是文档的名字是user，文档中具体的内容是通过`new mongoose.Schema`来定义的。

##### Mongoose文档类型

- String , Number等数据结构
- 定create, remove, update分别用来增、删、改的操作
- Find和findOne用来查询数据

##### 新增数据

```js
// 新增数据
User.create({
	username: 'imooc',
	age: 18
}, function(err, doc) {
	if (!err) {
		console.log(doc);
	}
	else {
		console.log(err);
	}
});
```

##### 查找数据

查找mongodb中的所有数据：

```js
User.find({}, function(err, doc) {
    res.json(doc);
});
```

##### 删除数据

删除mongodb中age为18的数据：

```js
User.remove({age: 18}, function(err, doc) {
    console.log(doc);
});
```

##### 更新数据

```js
User.update({username: 'hht'}, {'$set': {age: 26}}, function(err, doc) {
	console.log(doc);
});
```

## 第3章：React基础知识回顾

### 3-1: React基础知识回顾1-入门例子

- React16是第一个核心代码重写的版本,整体API变化不大

- 主要变更了错误处理、生命周期、打包,对开发影响不是特别大

- npm install --save react@next react-dom@next

  默认还是版本15 ,手动更新为16

#### React基础语法

- import React
- class语法新建组件, render里直接使用
- render函数返回值就是输出JSX语法，会把JSX转成js执行

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/39.png)

#### JSX基础语法

React的View层语法

- Js里直接写html
- Class要写成className
- 变量用{}包裹即可

#### 独立团项目

模拟李云龙管理独立团，学习React的Api

- 块一切都是组件
- 对组件间通信通过属性传递
- 类实现组件,使用JSX语法

##### 一个简单的组件

```jsx
// 引入React，必不可少
import React from 'react'

class App extends React.Component {
	render() {
		return <h2>独立团</h2>
	}
}

// 对外输出这个组件
export default App
```

注意，组件名首字母要大写。（这里是App）

注意：`return <h2>独立团</h2>`写的并不是HTML标签，而是jsx语法。实际执行的是一串js代码。

##### 渲染变量

```jsx
// 引入React，必不可少
import React from 'react'

class App extends React.Component {
	render() {
		const boss = '李云龙'
		return <h2>独立团, 团长{boss}</h2>
	}
}

// 对外输出这个组件
export default App
```

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/40.png)

可以看到，李云龙被渲染进去jsx里面了。

##### 组件之间嵌套使用

```jsx
// 引入React，必不可少
import React from 'react'

class App extends React.Component {
	render() {
		const boss = '李云龙'
		return (
			<div>
				<h2>独立团, 团长{boss}</h2>
				<Yiying></Yiying>
			</div>
		)
	}
}

class Yiying extends React.Component {
	render() {
		const boss = '张大喵'
		return <h2>一营营长，{boss}</h2>
	}
}

// 对外输出这个组件
export default App
```

注意，**一个组件只能返回一个根标签**，所以return后面需要跟一个()。

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/41.png)

### 3-2: React基础知识回顾2-组件之间传递数据

组件之间用props传递数据

- 使用`<组件 数据=“值”>`的形式传递
- 组件里使用`this.props`获取值
- 如果组件只有render函数,还可以用函数的形式写组件

```jsx
// 引入React，必不可少
import React from 'react'

class App extends React.Component {
	render() {
		const boss = '李云龙'
		return (
			<div>
				<h2>独立团, 团长{boss}</h2>
				<Yiying laoda='张大喵'></Yiying>
			</div>
		)
	}
}

class Yiying extends React.Component {
	render() {
		return <h2>一营营长，{this.props.laoda}</h2>
	}
}

// 对外输出这个组件
export default App
```

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/42.png)

### 3-3：React基础知识回顾3-组件内部

組件内部通辻state管理状恣

- JSX本庚就是js ,所以直接`数组.map`来喧染列表
- Constructor设置出事状态, 记得执行`super(props)`
- 如State就是一个不可变的对象,使用`this.state`获取

```jsx
// 引入React，必不可少
import React from 'react'

class App extends React.Component {
	render() {
		const boss = '李云龙'
		return (
			<div>
				<h2>独立团, 团长{boss}</h2>
				<Yiying laoda='张大喵'></Yiying>
			</div>
		)
	}
}

class Yiying extends React.Component {
	constructor(props) {
		super(props)
		this.state = {
			solders: ['huzi', 'zhuzi', 'wgs']
		}
	}

	render() {
		return (
			<div>
				<h2>一营营长，{this.props.laoda}</h2>
				<ul>
					{
						this.state.solders.map(v => {
							return <li key={v}>{v}</li>
						})
					}
				</ul>
			</div>
		)
	}
}

// 对外输出这个组件
export default App
```

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/43.png)

### 3-4：React基础知识回顾4-事件

##### onClick点击事件

- JSX里, `onClick={this.函数名}`来绑定事件
- this引用的问题,需要在构造函数里用bind绑定this
- `this.setState`修改state , **记得返回新的state ,而不是修改**

```jsx
// 引入React，必不可少
import React from 'react'

class App extends React.Component {
	render() {
		const boss = '李云龙'
		return (
			<div>
				<h2>独立团, 团长{boss}</h2>
				<Yiying laoda='张大喵'></Yiying>
			</div>
		)
	}
}

class Yiying extends React.Component {
	constructor(props) {
		super(props)
		this.state = {
			solders: ['huzi', 'zhuzi', 'wgs']
		}
		this.addSolder = this.addSolder.bind(this)
	}

	addSolder() {
		console.log('hello add solder')
		this.setState({
			solders: [...this.state.solders, '新兵蛋子' + Math.random()]
		})
	}

	render() {
		return (
			<div>
				<h2>一营营长，{this.props.laoda}</h2>
				<button onClick={this.addSolder}>新兵入伍</button>
				<ul>
					{
						this.state.solders.map(v => {
							return <li key={v}>{v}</li>
						})
					}
				</ul>
			</div>
		)
	}
}

// 对外输出这个组件
export default App
```

因为，当把`this.addSolder`函数传递给click事件的之后，直接执行，是无法在addSolder函数中找到`this`的。

第一种解决方法就是按照上面的代码所示，在构造函数中给addSolder绑定一下this：

```jsx
this.addSolder = this.addSolder.bind(this)
```

第二种解决方法是在click那里写箭头函数：

```jsx
<button onClick={() => this.addSolder()}>新兵入伍</button>
```

这样就不需要在构造函数中给每个函数绑定this了。

#### 3-5：React基础知识回顾5-React生命周期

React组件有若干钩子函数,在组件不同的状态执行

- 初始化周期
- 组件重新渲染生命周期
- 组件卸载声明周期

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/44.png)

例子：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/45.png)

结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/46.png)

可以看到，按照生命周期打印了这3条语句。

更加详细的周期：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/47.png)

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/48.png)

### 3-6：React基础知识回顾6-安装CHROME扩展

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/49.png)

### 3-7：antd-mobile组件使用

#### 安装

安装最新版：

```shell
npm install antd-mobile@next --save
```

我们安装的依赖可以在`node_modules`中找到：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/50.png)

注意，我们在导入的时候除了要把`antd-mobile`导入进来，还要把`antd-mobile.css`给导入进来，否则是没有样式的：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/51.png)

#### 按需加载

```shell
npm install babel-plugin-import --save
```

然后配置package.json：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/52.png)

这样的话，我们就不需要在文件中引入css样式了，也就是说，不需要这句：

```jsx
import 'antd-mobile/dist/antd-mobile.css'
```

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/53.png)

#### 其他示例

更多组件+按需加载

- 其他组件官网挨个展示
- 直接import会加载所有的组件,  需要自定义配置按需加载
- 个性化配置后面统一配置(需要执行npm run eject)

## 第4章：Redux状态管理与React-router

这种状态管理实际上是一个发布订阅的设计模式。

### 4-1 Redux状态管理1-结合小例子看 Redux 是什么？

#### Redux是什么

专注于**状态管理**的库

- Redux专注于状态管理,  和react解耦
- 单一状态,  单向数据流
- 核心概念:  store,  state,  action,  reducer

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/54.png)

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/55.png)

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/56.png)

#### 安装redux

```shell
npm install redux --save
```

#### 例子

我们先把src目录中的文件都删除，新建一个文件`index.js`。

然后，我们的代码如下：

```jsx
import {
	createStore
} from 'redux'
// 1. 新建store (通过reducer建立，根据老的state和action，生成新的state)
function counter(state = 0, action) {
	switch (action.type) {
		case '加机关枪':
			return state + 1
		case '减机关枪':
			return state - 1
		default:
			return 10
	}
}

const store = createStore(counter)

const init = store.getState()
console.log(init)
```

通过浏览器的调试窗口可以看到如下结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/57.png)

现在，我们派发事件：

```jsx
// 派发事件 (传递action)
store.dispatch({
	type: '加机关枪'
})
console.log(store.getState())
```

结果如下：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/58.png)

我们继续派发事件：

```jsx
store.dispatch({
	type: '减机关枪'
})
console.log(store.getState())
```

结果如下：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/59.png)

完整的代码如下：

```jsx
import {
	createStore
} from 'redux'
// 1. 新建store (通过reducer建立，根据老的state和action，生成新的state)
function counter(state = 0, action) {
	switch (action.type) {
		case '加机关枪':
			return state + 1
		case '减机关枪':
			return state - 1
		default:
			return 10
	}
}

const store = createStore(counter)

const init = store.getState()
console.log(init)

// 派发事件 (传递action)
store.dispatch({
	type: '加机关枪'
})
console.log(store.getState())

store.dispatch({
	type: '减机关枪'
})
console.log(store.getState())
```

但是，这一些有一点冗余，可以通过订阅的方式来进行操作，完整代码如下：

```jsx
import {
	createStore
} from 'redux'
// 1. 新建store (通过reducer建立，根据老的state和action，生成新的state)
function counter(state = 0, action) {
	switch (action.type) {
		case '加机关枪':
			return state + 1
		case '减机关枪':
			return state - 1
		default:
			return 10
	}
}

const store = createStore(counter)

const init = store.getState()
console.log(init)

function listener() {
	const current = store.getState()
	console.log(`现在有机枪${current}把`)
}

store.subscribe(listener)

// 派发事件 (传递action)
store.dispatch({
	type: '加机关枪'
})
store.dispatch({
	type: '减机关枪'
})
```

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/60.png)

每次状态改变，都会执行我们订阅的那个函数。

### 4-2 Redux状态管理2-Redux 如何和React一起用

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/62.png)

#### 例子

我们清空index.js文件里面的内容，写入如下代码：

```jsx
import React from 'react'
import ReactDom from 'react-dom'

ReactDom.render(<App />, document.getElementById('root'))
```

其中，root这个id是在`public/index.html`文件中：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/63.png)

实际上，我们能够看到的所有页面，都是把js注入到`public/index.html`文件里面。

然后，我们在文件`App.js`中编写我们的组件`App`：

```jsx
import React from 'react'

class App extends React.Component {
	// constructor() {
	// 	super(props)
	// }
	render() {
		return (
			<h1>现在有机枪</h1>
		)
	}
}

export default App
```

为了能够在`index.js`中使用我们的组件，我们需要在`index.js`文件中，导入这个组件：

```jsx
import React from 'react'
import ReactDom from 'react-dom'
import App from './App'

ReactDom.render(<App />, document.getElementById('root'))
```

现在，我们就可以在页面中看到如下结果：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/64.png)

此时，我们的页面还没有数据。接下来，我们编写和状态管理有关的代码。写在文件`index.redux.js`中：

```jsx
const ADD_GUN = '加机关枪'
const REMOVE_GUN = '减机关枪'

// reducer
export function counter(state = 0, action) {
	switch (action.type) {
		case ADD_GUN:
			return state + 1
		case REMOVE_GUN:
			return state - 1
		default:
			return 10
	}
}

// action creatore
export function addGUN() {
	return {
		type: ADD_GUN
	}
}

export function removeGUN() {
	return {
		type: REMOVE_GUN
	}
}
```

接下来，我们在`index.js`中使用：

```jsx
import React from 'react'
import ReactDom from 'react-dom'
import {
	counter
} from './index.redux.js'

import App from './App'
import {
	createStore
} from 'redux'

const store = createStore(counter)

function render() {
	ReactDom.render(<App store={store} />, document.getElementById('root'))
}

render()
```

可以看到，我们使用了`index.redux.js`中的`counter`这个reducer。

然后，我们通过redux的createStore方法，插件了一个仓库。并且，把这个仓库通过属性的形式，传递给了组件App。

接下来，我们在组件App中去使用这个仓库（在文件App.js里面）：

```jsx
import React from 'react'

class App extends React.Component {
	// constructor() {
	// 	super(props)
	// }
	render() {
		const store = this.props.store
		const num = store.getState()
		return (
			<h1>现在有机枪{num}把</h1>
		)
	}
}

export default App
```

在组件中，可以通过`this.props`来获取属性store，通过store的getState方法可以获取当前的状态值。

结果如下：

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/65.png)

接下来，我们开始去管理这个状态：

```jsx
import React from 'react'
import {
	addGUN
} from './index.redux.js'

class App extends React.Component {
	// constructor() {
	// 	super(props)
	// }
	render() {
		const store = this.props.store
		const num = store.getState()
		return (
			<div>
				<h1>现在有机枪{num}把</h1>
				<button onClick={() => store.dispatch(addGUN())}>申请武器</button>
			</div>
		)
	}
}

export default App
```

意思是，每次点击这个button，就会执行箭头函数，这个箭头函数的作用是执行函数store.dispatch，它可以增加武器的数量，也就是改变状态。

因为每次增加武器数量之后，状态就会改变，所以，我们需要在文件`index.js`中订阅一下：

```jsx
import React from 'react'
import ReactDom from 'react-dom'
import {
	counter
} from './index.redux.js'

import App from './App'
import {
	createStore
} from 'redux'

const store = createStore(counter)

function render() {
	ReactDom.render(<App store={store} />, document.getElementById('root'))
}

render()

store.subscribe(render)
```

每次状态改变，都会重新执行方法render()渲染页面。

### 4-3:  Redux状态管理4-更进一步,让Redux可以处理异步

但是，对于上面的代码会有一点问题。因为在文件`index.js`和组件`App.js`中都引入了`./index.redux.js`。我们希望组件是尽可能和外界无关的，因为我们设计组件的原则就是：组件尽可能的通用。

所以，我们只在文件`index.js`中引入`./index.redux.js`，通过属性的方式，把组件需要的东西传递给App这个组件：

```jsx
import React from 'react'
import ReactDom from 'react-dom'
import {
	counter,
	addGUN
} from './index.redux.js'

import App from './App'
import {
	createStore
} from 'redux'

const store = createStore(counter)

function render() {
	ReactDom.render(<App store={store} addGUN={addGUN} />, document.getElementById('root'))
}

render()

store.subscribe(render)
```

而组件内部，通过属性去获取传递进来的参数（文件App.js）：

```jsx
import React from 'react'

class App extends React.Component {
	// constructor() {
	// 	super(props)
	// }
	render() {
		const store = this.props.store
		const addGUN = this.props.addGUN
		const num = store.getState()
		return (
			<div>
				<h1>现在有机枪{num}把</h1>
				<button onClick={() => store.dispatch(addGUN())}>申请武器</button>
			</div>
		)
	}
}

export default App
```

这样，我们组件的内部就不依赖于外部的状态，只依赖于外部传递进来的参数。

### 4-4:  Redux状态管理4-更近一步,让Redux可以处理异步

处理异步、调试工具、更优雅的和react结合

- Redux处理异步,需要redux-thunk插件

  Redux默认只处理同步,异步任务需要react thunk中间件

- Npm install redux-devtools-extension 并且开启
- 使用react-redux优雅的链接react和redux

#### 安装redux-thunk

```shell
npm install redux-thunk --save
```

**使用applyMiddleware开启thunk中间件**。原来的Action只能返回一个对象，例如上面的：

```jsx
// action creatore
export function addGUN() {
	return {
		type: ADD_GUN
	}
}
```

有了redux-thunk插件之后，Action可以返回函数，使用dispatch提交action。

在`index.redux.js`中编写异步任务：

```jsx
export function addGunAsync() {
	// 箭头函数中的dispatch是参数
	return dispatch => {
		setTimeout(() => {
			dispatch(addGUN())
		}, 2000)
	}
}
```

#### 开启redux-thunk插件

使用applyMiddleware开启thunk中间件，并且导入这个异步的任务（文件index.js）：

```jsx
import React from 'react'
import ReactDom from 'react-dom'
import thunk from 'redux-thunk'

import {
	counter,
	addGUN,
	removeGUN,
	addGunAsync
} from './index.redux.js'
import App from './App'
import {
	createStore,
	applyMiddleware
} from 'redux'

const store = createStore(counter, applyMiddleware(thunk))

function render() {
	ReactDom.render(<App store={store} addGunAsync={addGunAsync} addGUN={addGUN} removeGUN={removeGUN}/>, document.getElementById('root'))
}

render()
store.subscribe(render)
```

#### 使用这个异步任务

```jsx
import React from 'react'

class App extends React.Component {
	// constructor() {
	// 	super(props)
	// }
	render() {
		const store = this.props.store
		const addGUN = this.props.addGUN
		const removeGUN = this.props.removeGUN
		const addGunAsync = this.props.addGunAsync
		const num = store.getState()
		return (
			<div>
				<h1>现在有机枪{num}把</h1>
				<button onClick={() => store.dispatch(addGUN())}>申请武器</button>
				<button onClick={() => store.dispatch(removeGUN())}>释放武器</button>
				<button onClick={() => store.dispatch(addGunAsync())}>拖两天再给</button>
			</div>
		)
	}
}

export default App
```

### 4-5：Redux状态管理5-Chrome中Redux调试工具

### 4-6: Redux状态管理6-使用 React-redux

老赵能力用起来很麻烦,为了方便管理,使用魏和尚来负责链接

- npm install react-redux --save
- 忘记subscribe,  记住reducer、action和dispatch即可
- React-redux提供Provider和connect两个接口来链接

#### React-redux具体使用

- Provider组件在应用最外层, 传入store即可,  只用一次
- Connect负责从外部获取组件需要的参数
- Connect可以用装饰器的方式来写

### 4-7 Redux状态管理7-使用 React-redux(Connect可以用装饰器的方法来书写)

使用装饰器优化connect代码

- npm run eject     弾出个性化配置

- npm install babel-plugin-transform-decorators-legacy --save

  这是一个专门支持装饰器的插件

- package.json里，babel部分加上plugins配置

### 4-8: React-router4 路由 01-初识 React-router4

#### Redux-router4是什么

React官方推荐路由库, 4是最新版本

- 4是全新的版本,和之前版本不兼容,浏览器和RN均兼容
- React开发单页应用必备,践行路由即组件的概念
- 核心概念:动态路由、Route、 Link、 Switch

#### 安装

```shell
npm install react-router-dom --save
```

Router4使用react-router-dom作为浏览器端的路由

#### 入门组件

- BrowserRouter,  包裹整个应用
- Router路由对应渲染的组件,  可嵌套
- Link跳转专用

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/66.png)

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/67.png)

### 4-9：React-router4 路由 02-React-router4 其他组件

- url参数, Route组件参数可用冒号标识参数
- Redirect组件跳转
- Switch只渲染一个子Route组件

### 4-10:  React-router4 路由 03-和 Redux配合-复杂 Redux应用1



### 4-11:  React-router4 路由 04-和Redux配合-复杂 Redux应用2

![](http://oklbfi1yj.bkt.clouddn.com/Redux+React%C2%A0Router+Node.js%E5%85%A8%E6%A0%88%E5%BC%80%E5%8F%91/68.png)







