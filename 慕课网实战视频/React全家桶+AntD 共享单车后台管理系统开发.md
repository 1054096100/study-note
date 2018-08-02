# React全家桶+AntD 共享单车后台管理系统开发

## 第2章 React基础知识

### 2-1 React基础介绍

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/1.png)

单向数据流之间数据的传递必须是有继承关系的，而没有继承关系的组件要实现数据传递，必须要借助redux来实现。

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/2.png)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/3.png)

声明式实现只需要声明我们的变量即可，不需要写出页面如何渲染（如何渲染是由框架底层实现的）

### 2-2 React脚手架使用

我们不可能每个项目都从0开始构建，我们需要一个辅助性的工具来初始化一些配置。

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/4.png)

#### 如何安装React脚手架

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/5.png)

`-g`代表全局安装，这样，我们可以在任何目录执行这个脚手架的命令。

#### Yarn

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/6.png)

Yarn不是去颠覆npm，而是去修复npm的一些缺陷。

##### 如何使用Yarn

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/7.png)

因为是单页面的程序，它只会构建一个组件，一个根组件会构建在`index.html`中的root里面。剩下的那些子组件都是挂在App.js里面。

### 2-3 React生命周期介绍

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/8.png)

#### 启动项目方法

```shell
yarn start
```

#### 一个小例子

父组件：

```jsx
import React from 'react'
import Child from './Child'

export default class Life extends React.Component {
	constructor(props) {
		super(props)
		this.state = {
			count: 0
		}
	}

	hadnleAdd = () => {
		this.setState({
			count: this.state.count + 1
		})
	}

	render() {
		return (
			<div>
				<p>React 生命周期介绍</p>
				<button onClick={this.hadnleAdd}>click</button>
				<p>{this.state.count}</p>
				<Child name='Jack'></Child>
			</div>
		)
	}
}
```

子组件：

```jsx
import React from "react";

export default class Child extends React.Component {
    constructor(props) {
        super(props)
        this.state = {
            count: 0
        }
    }
    
   componentWillMount() {
       console.log('will mount')
   }

   componentDidMount() {
    console.log('did mount')
   }
    
   componentWillReceiveProps(nextProps) {
       console.log('will props' + nextProps.name)
   }

   shouldComponentUpdate(nextProps, nextState) {
       console.log('should update')
       return true
   }

   componentWillUpdate(nextProps, nextState) {
       console.log('will update')
   }

    render() {
        return (
            <div>
                <p>{this.props.name}</p>
            </div>
        )
    }
}
```

## 第3章 主页面架构设计

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/9.png)

### 3-1基础插件安装(1)

基础插件安装，Less文件加载配置

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/10.png)

#### 安装

```shell
yarn add react-router-dom axios less-loader
```

react-router-dom指的是react-router和HTML的dom混合使用。而react-router是一个基础的路由，react-router-dom是在react-router之上的(也就是说拥有react-router的功能，甚至功能更多)，用于浏览器端的路由。

#### 暴露配置文件

antd是基于less开发的（注意，如果使用css文件的话，那么要用className而不是class），而脚手架生成的项目是不支持less的，所以需要我们自己去配置。

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/11.png)

此时，package.json里面就显示出了很多依赖。（之前就没有显示）

(注意，每次改完配置之后都需要重新启动node服务器)

### 3-2基础插件安装(2)

```shell
yarn add antd
```

然后，我们在Life.js中使用antd里面的组件：

```jsx
import React from 'react'
import Child from './Child'
import {Button} from 'antd'
import './index.less'
import 'antd/dist/antd.css'

export default class Life extends React.Component {
	constructor(props) {
		super(props)
		this.state = {
			count: 0
		}
	}

	hadnleAdd = () => {
		this.setState({
			count: this.state.count + 1
		})
	}

	render() {
		return (
			<div className='content'>
				<p>React 生命周期介绍</p>
				<Button onClick={this.hadnleAdd}>click</Button>
				<p>{this.state.count}</p>
				<Child name='Jack'></Child>
			</div>
		)
	}
}
```

按需加载antd的样式：

```shell
yarn add babel-plugin-import
```

然后配置webpack，这样的话就不需要引入antd.css文件了。这样就可以减少文件的请求量，提高我们的性能。

#### 安装less指定版本

```shell
yarn add less@^2.7.3
```

### 3-3页面结构开发(1)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/12.png)

拿到一个页面，不要急着写代码，一定要理清页面由哪些部分组成。

区分好组件和页面两者的关系：页面是我们可以看到的页面，组件是可以被页面引用的。

项目的架构，也就是说要决定我们的目录：

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/13.png)

### 3-4页面结构开发(2)

开发左边的侧边栏：

```jsx
import React from 'react'

export default class NavLeft extends React.Component {
    render() {
        return(
            <div style={{ backgroundColor: 'red' }}>
                This is NavLeft
            </div>
        )
    }
}
```

`style={{ backgroundColor: 'red' }}`这里使用两个大括号的原因是style后面的要是一个对象，所以需要使用`{ backgroundColor: 'red' }`，并且，对于js语法，我们需要通过一对大括号去解析，所以又需要一对大括号，因此这里需要两个大括号。实际上，这个等价于：

```jsx
import React from 'react'

export default class NavLeft extends React.Component {
    render() {
        var style = {
            backgroundColor: 'red'
        }
        return(
            <div style={style}>
                This is NavLeft
            </div>
        )
    }
}
```

此时，页面结果是：

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/14.png)

为了让侧边栏撑满整个高度，我们需要使用计算属性，此时，我们建立一个全局的样式：

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/15.png)

使用less的好处就是可以嵌套，并且可以定义变量。

```less
.container {
    display: flex;
    .nav-left {
        width: 15%;
        min-width: 180px;
        height: calc(100vh);
        background-color: red;
    }
    .main {
        height: calc(100vh);
        flex: 1;
    }
    .content {
        position: relative;
        padding: 20px;
    }
}
```

其中的calc是用于动态计算长度值，例如：

```less
width: calc(100% - 10px);
```

也就是说，整个屏幕的宽度减去10px。需要注意的是运算符前后都需要保留一个空格。

任何长度值都可以使用calc()函数进行计算;
calc()函数支持`"+", "-", "*", "/"`运算;
calc()函数使用标准的数学运算优先级规则; 

100vh相当于是100%的意思。

### 3-5菜单组件开发(1)

#### 填充侧边栏的标题

我们写一个配置文件，文件中的内容为：

```jsx
const menuList = [
    {
        title:'首页',
        key:'/home'
    },
    {
        title:'UI',
        key:'/ui',
        children:[
            {
                title:'按钮',
                key:'/ui/buttons',
            },
            {
                title:'弹框',
                key:'/ui/modals',
            },
            {
                title:'Loading',
                key:'/ui/loadings',
            },
            {
                title:'通知提醒',
                key:'/ui/notification',
            },
            {
                title:'全局Message',
                key:'/ui/messages',
            },
            {
                title:'Tab页签',
                key:'/ui/tabs',
            },
            {
                title:'图片画廊',
                key:'/ui/gallery',
            },
            {
                title:'轮播图',
                key:'/ui/carousel',
            }
        ]
    },
    {
        title:'表单',
        key:'/form',
        children:[
            {
                title:'登录',
                key:'/form/login',
            },
            {
                title:'注册',
                key:'/form/reg',
            }
        ]
    },
    {
        title:'表格',
        key:'/table',
        children:[
            {
                title:'基础表格',
                key:'/table/basic',
            },
            {
                title:'高级表格',
                key:'/table/high',
            }
        ]
    },
    {
        title:'富文本',
        key:'/rich'
    },
    {
        title:'城市管理',
        key:'/city'
    },
    {
        title:'订单管理',
        key:'/order',
        btnList:[
            {
                title:'订单详情',
                key:'detail'
            },
            {
                title:'结束订单',
                key:'finish'
            }
        ]
    },
    {
        title:'员工管理',
        key:'/user'
    },
    {
        title:'车辆地图',
        key:'/bikeMap'
    },
    {
        title:'图标',
        key:'/charts',
        children:[
            {
                title:'柱形图',
                key:'/charts/bar'
            },
            {
                title:'饼图',
                key:'/charts/pie'
            },
            {
                title:'折线图',
                key:'/charts/line'
            },
        ]
    },
    {
        title:'权限设置',
        key:'/permission'
    },
];

export default menuList;
```

### 3-6菜单组件开发(2)

```jsx
import React from 'react'
import { Menu, Icon } from 'antd'
import './index.less'
import MenuConfig from './../../config/menuConfig'

const SubMenu = Menu.SubMenu


export default class NavLeft extends React.Component {
    
    componentWillMount() {
        const menuTreeNode = this.renderMenu(MenuConfig)
        this.setState({
            menuTreeNode
        })
    }

    // 菜单渲染
    renderMenu = (data) => {
        return data.map((item) => {
            if (item.children) {
                return (
                    <SubMenu title={item.title} key={item.key}>
                        {this.renderMenu(item.children)}
                    </SubMenu>
                )

            }
            return <Menu.Item title={item.title} key={item.key} >{item.title}</Menu.Item>
        })
    }
    
    render() {
        return(
            <div>
                <div className='logo'>
                    <img src='' alt=''/>
                    <h1>KeenOTA</h1>
                </div>
                <Menu
                    theme='dark'
                >
                    {this.state.menuTreeNode}
                </Menu>
            </div>
        )
    }
}
```

当我们去调用`setState`函数的时候，render函数会被执行。（如果我们要使用某个变量，那么我们需要把变量放在`setState`函数中）

渲染的时候，需要使用递归来把子列表显示出来。

### 3-7头部组件实现(1)

```jsx
import React from 'react'
import { Row, Col } from 'antd';
import './index.less'
import Util from '../../utils/utils'

export default class Header extends React.Component {
    componentWillMount() {
        this.setState({
            userName: '黄汉韬'
        })
        setInterval(() => {
            let sysTime = Util.formateDate(new Date().getTime())
            this.setState({
                sysTime
            })
        }, 1000)
    }

    render() {
        return(
            <div className='header'>
                <Row className='header-top'>
                    <Col span='24'>
                        <span>welcome {this.state.userName}</span>
                        <a href='#'>退出</a>
                    </Col>
                </Row>
                <Row className='breadcrumb'>
                    <Col span='4' className='breadcrumb-title'>
                        首页
                    </Col>
                    <Col span='20' className='weather'>
                        <span className='date'>{this.state.sysTime}</span>
                        <span className='weather-detail'>天气</span>
                    </Col>
                </Row>
            </div>
        )
    }
}
```

```jsx
.header {
    .header-top {
        height: 60px;
        line-height: 60px;
        padding: 0 20px;
        text-align: right;
        a {
            margin-left: 40px;
        }
    }
    .breadcrumb {
        height: 40px;
        line-height: 40px;
        padding: 0 20px;
        border-top: 1px solid #f9c700;
        .breadcrumb-title {
            text-align: center;
        }
        .weather {
            text-align: right;
            .date {
                margin-right: 10px;;
            }
        }
    }
}
```

### 3-8头部组件实现(2)

#### 安装jsonp

```shell
yarn add jsonp --save
```

#### 封装jsonp

```jsx
import JsonP from 'jsonp'

export default class Axios {
    static jsonp(options) {
        return new Promise((resolve, reject) => {
            JsonP(options.url, {
                param: 'callback'
            }, function(err, response) {
                if (response.status == 'success') {
                    resolve(response)
                }
                else {
                    reject(response.message)
                }
            })
        })
    }
}
```

json是一定需要callback的。

### 3-9底部组件功能实现(1)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/16.png)

我们把内容区称为页面而不是组件。因为，当我们点击侧边栏中的链接的时候，内容区的内容是会变的，所以我们把内容区称为页面，而那些固定不变的就称为组件，例如Header、侧边栏、Footer。

#### 让内容区域中的文字水平居中

```less
.home-wrap {
    height: calc(60%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
}
```

其中，`align-items`控制垂直居中，`justify-content`控制水平居中。

对于页面中的一些图形图标，例如三角形，一般使用绝对定位来控制，并且通过伪类来实现。

## 第4章Router 4.0路由实战演练

### 4-1 React Router 4.0路由基本介绍

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/17.png)

4.0版本的路由，可以放在任何一个页面或者组件内部来进行使用。

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/18.png)

#### 路由模块安装

```shell
yarn add react-router-dom
```

#### react-router-dom核心用法

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/19.png)

#### HashRouter和BrowserRouter

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/20.png)

#### Route用法

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/21.png)

#### Link

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/22.png)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/23.png)

#### Switch

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/24.png)

Switch指的是按顺序匹配，一旦匹配到一个路由之后，就不会去匹配后面的路由了。而exact指的是精准匹配某个路由。所以，两者是有区别的。

#### Redirect

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/25.png)

### 4-2 React-Router4.0 路由Demo演示（1）

```jsx
import React from 'react'
import {HashRouter, Route, Link, Switch} from 'react-router-dom'
import Main from './main'
import About from './about'
import Topics from './topic'

export default class Home extends React.Component {
    render() {
        return(
            <HashRouter>
                <div>
                    <ul>
                        <li><Link to="/">Home</Link></li>
                        <li><Link to="/about">About</Link></li>
                        <li><Link to="/topics">Topics</Link></li>
                    </ul>
                    <hr/>
                    <Switch>
                        <Route path='/' exact={true} component={Main}></Route>
                        <Route path='/about' component={About}></Route>
                        <Route path='/topics' component={Topics}></Route>
                    </Switch>
                </div>  
            </HashRouter>
        )
    }
}
```

HashRouter只能有一个根节点，所以这里有一个`div`把它们包围了。

### 4-3 React-Router4.0 路由Demo演示（2）

```jsx
import React from 'react'
import {HashRouter as Router, Route, Link} from 'react-router-dom'
import Main from './../route1/main'
import About from './../route1/about'
import Topics from './../route1/topic'
import Home from './home'

export default class IRouter extends React.Component {
    render() {
        return(
            <Router>
                <Home>
                    <Route path='/' exact={true} component={Main}></Route>
                    <Route path='/about' component={About}></Route>
                    <Route path='/topics' component={Topics}></Route>
                </Home>
            </Router>
        )
    }
}
```

```jsx
import React from 'react'
import {Link} from 'react-router-dom'

export default class Home extends React.Component {
    render() {
        return(
            <div>
                <ul>
                    <li><Link to="/">Home1</Link></li>
                    <li><Link to="/about">About1</Link></li>
                    <li><Link to="/topics">Topics1</Link></li>
                </ul>
                <hr/>
                {this.props.children}
            </div>  
        )
    }
}
```

### 4-4 React-Router4.0 Demo2 演示

获取路由中的值。

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/26.png)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/27.png)

### 4-5 React Router4.0在项目当中的运用

首先，我们在入口文件index.js中配置router，否则我们的页面不知道如何跳转：

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
// import Life from './pages/demo/Life';
import Admin from './admin'
import Router from './router'
import registerServiceWorker from './registerServiceWorker';

ReactDOM.render(<Router />, document.getElementById('root'));
registerServiceWorker();
```

然后，我们在router文件中定义我们的路由：

```jsx
import React from 'react'
import {HashRouter, Route, Switch} from 'react-router-dom'
import App from './App'
import Login from './pages/login'
import Admin from './admin'
import Buttons from './pages/ui/buttons'
import NoMatch from './pages/nomatch'

export default class IRouter extends React.Component {
    render() {
        return(
            <HashRouter>
                <App>
                    <Route path='/login' component={Login} />
                    <Route path='/admin' render={()=>
                        <Admin>
                            <Route path='/admin/ui/buttons' component={Buttons} />
                            <Route component={NoMatch} />
                        </Admin>
                    } />
                    <Route path='/order/detail' component={Login} />
                </App>
            </HashRouter>
        )
    }
}
```

我们需要先定义我们使用的路由方式，这里是`HashRouter`。然后，加载根组件`App`（因为我们要有登陆页面、内容管理页面、详情页面，所以我们需要有根组件）

## 第5章 UI菜单各个组件使用

### 5-1 Button按钮使用讲解(1)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/28.png)

#### 按钮

```jsx
import React from 'react'
import { Card, Button } from 'antd';
import './ui.less'

export default class Buttons extends React.Component {
    render() {
        return(
            <div>
                <Card title='基础按钮' >
                    <Button type='primary' >Keen</Button>
                    <Button>Keen</Button>
                    <Button type='dashed' >Keen</Button>
                    <Button type='danger' >Keen</Button>
                    <Button disabled >Keen</Button>
                </Card>
                <Card title='图形按钮' >
                    <Button icon='plus' >创建</Button>
                    <Button icon='edit' >编辑</Button>
                    <Button icon='delete' >删除</Button>
                    <Button shape='circle' icon='search' ></Button>
                    <Button type='primary' icon='search' >搜索</Button>
                    <Button type='primary' icon='download' >下载</Button>
                </Card>
                <Card title='Loading按钮' >
                    <Button type='primary' loading={true} >确定</Button>
                    <Button type='primary' shape='circle' loading={true} ></Button>
                    <Button loading={true} >点击加载</Button>
                    <Button shape='circle' loading={true} ></Button>
                    <Button type='primary' onClick={this.handleCloseLoading} >关闭</Button>
                </Card>
            </div>
        )
    }
}
```

### 5-2 Button按钮使用讲解(2)

#### 取消按钮加载的效果

```jsx
import React from 'react'
import { Card, Button } from 'antd';
import './ui.less'

export default class Buttons extends React.Component {
    state = {
        loading: true
    }
    handleCloseLoading = () => {
        this.setState({
            loading: false
        })
    }

    render() {
        return(
            <div>
                <Card title='基础按钮' >
                    <Button type='primary' >Keen</Button>
                    <Button>Keen</Button>
                    <Button type='dashed' >Keen</Button>
                    <Button type='danger' >Keen</Button>
                    <Button disabled >Keen</Button>
                </Card>
                <Card title='图形按钮' >
                    <Button icon='plus' >创建</Button>
                    <Button icon='edit' >编辑</Button>
                    <Button icon='delete' >删除</Button>
                    <Button shape='circle' icon='search' ></Button>
                    <Button type='primary' icon='search' >搜索</Button>
                    <Button type='primary' icon='download' >下载</Button>
                </Card>
                <Card title='Loading按钮' >
                    <Button type='primary' loading={this.state.loading} >确定</Button>
                    <Button type='primary' shape='circle' loading={this.state.loading} ></Button>
                    <Button loading={true} >点击加载</Button>
                    <Button shape='circle' loading={this.state.loading} ></Button>
                    <Button type='primary' onClick={this.handleCloseLoading} >关闭</Button>
                </Card>
            </div>
        )
    }
}
```

#### 按钮组

```jsx
import React from 'react'
import { Card, Button, Radio } from 'antd';
import './ui.less'

export default class Buttons extends React.Component {
    state = {
        loading: true,
        size: 'default'
    }
    handleCloseLoading = () => {
        this.setState({
            loading: false
        })
    }

    handleChange = (e) => {
        this.setState({
            size: e.target.value // 这里的e代表被鼠标点击的对象
        })
    }

    render() {
        return(
            <div>
                <Card title='基础按钮' className='card-wrap' >
                    <Button type='primary' >Keen</Button>
                    <Button>Keen</Button>
                    <Button type='dashed' >Keen</Button>
                    <Button type='danger' >Keen</Button>
                    <Button disabled >Keen</Button>
                </Card>
                <Card title='图形按钮' className='card-wrap' >
                    <Button icon='plus' >创建</Button>
                    <Button icon='edit' >编辑</Button>
                    <Button icon='delete' >删除</Button>
                    <Button shape='circle' icon='search' ></Button>
                    <Button type='primary' icon='search' >搜索</Button>
                    <Button type='primary' icon='download' >下载</Button>
                </Card>
                <Card title='Loading按钮' className='card-wrap' >
                    <Button type='primary' loading={this.state.loading} >确定</Button>
                    <Button type='primary' shape='circle' loading={this.state.loading} ></Button>
                    <Button loading={true} >点击加载</Button>
                    <Button shape='circle' loading={this.state.loading} ></Button>
                    <Button type='primary' onClick={this.handleCloseLoading} >关闭</Button>
                </Card>
                <Card title='按钮组' >
                    <Button.Group>
                        <Button type='primary' icon='left' >返回</Button>
                        <Button type='primary' icon='right' >前进</Button>
                    </Button.Group>
                </Card>
                <Card title='按钮尺寸' className='card-wrap' >
                    <Radio.Group value={this.state.size} onChange={this.handleChange} >
                        <Radio value='small' >小</Radio>
                        <Radio value='default' >中</Radio>
                        <Radio value='large' >大</Radio>
                    </Radio.Group>
                    <Button type='primary' size={this.state.size} >Keen</Button>
                    <Button size={this.state.size} >Keen</Button>
                    <Button type='dashed' size={this.state.size} >Keen</Button>
                    <Button type='danger' size={this.state.size} >Keen</Button>
                </Card>
            </div>
        )
    }
}
```

### 5-3 Moda1组件使用讲解(1)

```jsx
import React from 'react'
import './ui.less'
import { Card, Button, Modal } from 'antd';

export default class Modals extends React.Component {
    state = {
        showModal1: false,
        showModal2: false,
        showModal3: false,
        showModal4: false,
    }

    handleOpen = (type) => {
        this.setState({
            [type]: true
        })
    }

    render() {
        return(
            <div>
                <Card title='基础模态框' className='card-wrap' >
                    <Button type='primary' onClick={() => this.handleOpen('showModal1')} >Open</Button>
                    <Button type='primary' onClick={() => this.handleOpen('showModal2')} >自定义页脚</Button>
                    <Button type='primary' onClick={() => this.handleOpen('showModal3')} >顶部20px弹框</Button>
                    <Button type='primary' onClick={() => this.handleOpen('showModal4')} >水平垂直居中</Button>
                </Card>
                <Modal
                    title='React'
                    visible={this.state.showModal1}
                    onCancel={() => {
                        this.setState({
                            showModal1: false
                        })
                    }}
                >
                    <p>
                        Welcome to KeenOTA
                    </p>

                </Modal>
            </div>
        )
    }
}
```

其中，这里有个小技巧：

```jsx
handleOpen = (type) => {
    this.setState({
        [type]: true
    })
}
```

我们可以使用`[type]`来解析传入进来的变量，而不用使用4个if来进行参数的判断。

### 5-4 Modal组件使用讲解(2)

#### 信息确认框

```jsx
import React from 'react'
import './ui.less'
import { Card, Button, Modal } from 'antd';

export default class Modals extends React.Component {
    state = {
        showModal1: false,
        showModal2: false,
        showModal3: false,
        showModal4: false,
    }

    handleOpen = (type) => {
        this.setState({
            [type]: true
        })
    }

    handleConfirm = (type) => {
        Modal[type]({
            title: '确认？',
            content: '你确定你学会了React了吗？',
            onOk() {
                console.log('ok')
            },
            onCancel() {
                console.log('cancel')
            }
        })
    }

    render() {
        return(
            <div>
                <Card title='基础模态框' className='card-wrap' >
                    <Button type='primary' onClick={() => this.handleOpen('showModal1')} >Open</Button>
                    <Button type='primary' onClick={() => this.handleOpen('showModal2')} >自定义页脚</Button>
                    <Button type='primary' onClick={() => this.handleOpen('showModal3')} >顶部20px弹框</Button>
                    <Button type='primary' onClick={() => this.handleOpen('showModal4')} >水平垂直居中</Button>
                </Card>
                <Card title='信息确认框' className='card-wrap' >
                    <Button type='primary' onClick={() => this.handleConfirm('confirm')} >Confirm</Button>
                    <Button type='primary' onClick={() => this.handleConfirm('info')} >Info</Button>
                    <Button type='primary' onClick={() => this.handleConfirm('success')} >Success</Button>
                    <Button type='primary' onClick={() => this.handleConfirm('warning')} >Warning</Button>
                </Card>
                <Modal
                    title='React'
                    visible={this.state.showModal1}
                    onCancel={() => {
                        this.setState({
                            showModal1: false
                        })
                    }}
                >
                    <p>
                        Welcome to KeenOTA
                    </p>
                </Modal>
                <Modal
                    title='React'
                    visible={this.state.showModal2}
                    cancelText='算了'
                    okText='好的'
                    onCancel={() => {
                        this.setState({
                            showModal2: false
                        })
                    }}
                >
                    <p>
                        Welcome to KeenOTA
                    </p>
                </Modal>
                <Modal
                    title='React'
                    visible={this.state.showModal3}
                    
                    onCancel={() => {
                        this.setState({
                            showModal3: false
                        })
                    }}
                >
                    <p>
                        Welcome to KeenOTA
                    </p>
                </Modal>
                <Modal
                    title='React'
                    visible={this.state.showModal4}
                    onCancel={() => {
                        this.setState({
                            showModal4: false
                        })
                    }}
                >
                    <p>
                        Welcome to KeenOTA
                    </p>
                </Modal>
            </div>
        )
    }
}
```

注意：

```jsx
<Button type='primary' onClick={() => this.handleConfirm('info')} >Info</Button>
```

这里不要写出

```jsx
<Button type='primary' onClick={this.handleConfirm('info')} >Info</Button>
```

因为这样会去执行`handleConfirm`函数（因此就会导致按钮还没被点击，`handleConfirm`函数就一直循环的执行下去），而不是去给button绑定点击事件。

### 5-5 Loading组件使用

```jsx
import React from 'react'
import { Card, Spin, Icon, Alert } from 'antd';
import './ui.less'

export default class Loadings extends React.Component {
    render() {
        const icon = <Icon type='loading' style={{fontSize: 24}} />
        return(
            <div>
                <Card title='Spin用法' className='card-wrap' >
                    <Spin size='small' />
                    <Spin style={{margin: '0 10px'}}  />
                    <Spin size='large'  />
                    <Spin indicator={icon} style={{marginLeft: 10}} />
                </Card>
                <Card title='内容遮罩' className='card-wrap' >
                    <Alert
                        message='React'
                        description='欢迎使用KeenOTA'
                        type='info'
                    />
                    <Spin>
                        <Alert
                            message='React'
                            description='欢迎使用KeenOTA'
                            type='warning'
                        />
                    </Spin>
                    <Spin tip='加载中...' >
                        <Alert
                            message='React'
                            description='欢迎使用KeenOTA'
                            type='warning'
                        />
                    </Spin>
                </Card>
            </div>
        )
    }
}
```

### 5-6 Notification组件使用

```jsx
import React from 'react'
import './ui.less'
import { Card, Button, notification } from 'antd';

export default class Notice extends React.Component {
    openNotification = (type, direction) => {
        if (direction) {
            notification.config({
                placement: direction
            })
        }
        notification[type]({
            message: '发工资了',
            description: '上个月考勤22天，迟到12天，实发工资250,请笑纳'
        })
    }

    render() {
        return(
            <div>
                <Card title='通知提醒框' className='card-wrap' >
                    <Button type='primary' onClick={() => this.openNotification('success')} >Success</Button>
                    <Button type='primary' onClick={() => this.openNotification('info')} >Info</Button>
                    <Button type='primary' onClick={() => this.openNotification('warning')} >Warning</Button>
                    <Button type='primary' onClick={() => this.openNotification('error')} >Error</Button>
                </Card>
                <Card title='通知提醒框' className='card-wrap' >
                    <Button type='primary' onClick={() => this.openNotification('success', 'topLeft')} >Success</Button>
                    <Button type='primary' onClick={() => this.openNotification('info', 'topRight')} >Info</Button>
                    <Button type='primary' onClick={() => this.openNotification('warning', 'bottomLeft')} >Warning</Button>
                    <Button type='primary' onClick={() => this.openNotification('error', 'bottomRight')} >Error</Button>
                </Card>
            </div>
        )
    }
}
```

### 5-7 Message组件使用

用于用户操作后的简短提示，比如说删除成功，给一个小的提示。

```jsx
import React from 'react'
import './ui.less'
import { Card, Button, message } from 'antd';

export default class Messages extends React.Component {
    showMessage = (type) => {
        message[type]('恭喜你，使用KeenOTA')
    }
    render() {
        return (
            <div>
                <Card title='全局提示框' className='card-wrap' >
                    <Button type='primary' onClick={() => this.showMessage('success')} >Success</Button>
                    <Button type='primary' onClick={() => this.showMessage('info')} >Info</Button>
                    <Button type='primary' onClick={() => this.showMessage('warning')} >Warning</Button>
                    <Button type='primary' onClick={() => this.showMessage('error')} >Error</Button>
                    <Button type='primary' onClick={() => this.showMessage('loading')} >Loading</Button>
                </Card>
            </div>
        )
    }
}
```

### 5- 8 Tabs组件使用(1)

```jsx
import React from 'react'
import './ui.less'
import { Card, Tabs, message, Icon } from 'antd';

const TabPane = Tabs.TabPane

export default class TabsAlias extends React.Component {
    handleCallback = (key) => {
        message.info('Hi, 您选择了页签：' + key)
    }
    
    componentWillMount() {
        const panes = [
            {
                title: 'Tab 1',
                content: 'Tab 1',
                key: '1'
            },
            {
                title: 'Tab 2',
                content: 'Tab 2',
                key: '2'
            },
            {
                title: 'Tab 3',
                content: 'Tab 3',
                key: '3'
            }
        ]
        this.setState({
            panes
        })
    }
    
    render() {
        return (
            <div>
                <Card title='Tab页签' className='card-wrap' >
                    <Tabs defaultActiveKey='1' onChange={this.handleCallback} >
                        <TabPane tab='Tab 1' key='1' >Content of Tab Pane 1</TabPane>
                        <TabPane tab='Tab 2' key='2' disabled >Content of Tab Pane 2</TabPane>
                        <TabPane tab='Tab 3' key='3' >Content of Tab Pane 3</TabPane>
                    </Tabs>
                </Card>
                <Card title='Tab带图的页签' className='card-wrap' >
                    <Tabs defaultActiveKey='1' onChange={this.handleCallback} >
                        <TabPane tab={<span><Icon type='plus' />Tab 1</span>} key='1' >Content of Tab Pane 1</TabPane>
                        <TabPane tab={<span><Icon type='edit' />Tab 2</span>} key='2' >Content of Tab Pane 2</TabPane>
                        <TabPane tab={<span><Icon type='delete' />Tab 3</span>} key='3' >Content of Tab Pane 3</TabPane>
                    </Tabs>
                </Card>
                <Card title='Tab带图的页签' className='card-wrap' >
                    <Tabs defaultActiveKey='1' onChange={this.handleCallback} >
                        {
                            this.state.panes.map((panel) => {
                                return <TabPane
                                    tab={panel.title}
                                    key={panel.key}
                                />
                            })
                        }
                    </Tabs>
                </Card>
            </div>
        )
    }
}
```

### 5- 9 Tabs组件使用(2)

```jsx
import React from 'react'
import './ui.less'
import { Card, Tabs, message, Icon } from 'antd';

const TabPane = Tabs.TabPane

export default class TabsAlias extends React.Component {
    newTabIndex = 0

    handleCallback = (key) => {
        message.info('Hi, 您选择了页签：' + key)
    }
    
    componentWillMount() {
        const panes = [
            {
                title: 'Tab 1',
                content: 'Tab 1',
                key: '1'
            },
            {
                title: 'Tab 2',
                content: 'Tab 2',
                key: '2'
            },
            {
                title: 'Tab 3',
                content: 'Tab 3',
                key: '3'
            }
        ]
        this.setState({
            activeKey: panes[0].key,
            panes
        })
    }

    onChange = (activeKey) => {
        this.setState({
            activeKey
        })
    }

    onEdit = (targetKey, action) => {
        this[action](targetKey)
    }

    add = () => {
        const panes = this.state.panes;
        const activeKey = `Tab ${this.newTabIndex++}`;
        panes.push({ title: activeKey, content: 'New Tab Pane', key: activeKey });
        this.setState({ panes, activeKey });
    }
    remove = (targetKey) => {
        let activeKey = this.state.activeKey;
        let lastIndex;

        this.state.panes.forEach((pane, i) => {
            if (pane.key === targetKey) {
                lastIndex = i - 1;
            }
        });
        const panes = this.state.panes.filter(pane => pane.key !== targetKey);
        if (lastIndex >= 0 && activeKey === targetKey) {
            activeKey = panes[lastIndex].key;
        }

        this.setState({ panes, activeKey });
    }
    
    render() {
        return (
            <div>
                <Card title='Tab页签' className='card-wrap' >
                    <Tabs defaultActiveKey='1' onChange={this.handleCallback} >
                        <TabPane tab='Tab 1' key='1' >Content of Tab Pane 1</TabPane>
                        <TabPane tab='Tab 2' key='2' disabled >Content of Tab Pane 2</TabPane>
                        <TabPane tab='Tab 3' key='3' >Content of Tab Pane 3</TabPane>
                    </Tabs>
                </Card>
                <Card title='Tab带图的页签' className='card-wrap' >
                    <Tabs defaultActiveKey='1' onChange={this.handleCallback} >
                        <TabPane tab={<span><Icon type='plus' />Tab 1</span>} key='1' >Content of Tab Pane 1</TabPane>
                        <TabPane tab={<span><Icon type='edit' />Tab 2</span>} key='2' >Content of Tab Pane 2</TabPane>
                        <TabPane tab={<span><Icon type='delete' />Tab 3</span>} key='3' >Content of Tab Pane 3</TabPane>
                    </Tabs>
                </Card>
                <Card title='Tab带图的页签' className='card-wrap' >
                    <Tabs 
                        onChange={this.onChange}
                        activeKey={this.state.activeKey}
                        type='editable-card'
                        onEdit={this.onEdit}
                    >
                        {
                            this.state.panes.map((panel) => {
                                return <TabPane
                                    tab={panel.title}
                                    key={panel.key}
                                />
                            })
                        }
                    </Tabs>
                </Card>
            </div>
        )
    }
}
```

### 5-12 Carousel组件使用(轮播图)

```jsx
import React from 'react'
import { Card, Carousel } from 'antd';
import './ui.less'

export default class Carouselalias extends React.Component {
    render() {
        return (
            <div>
                <Card title='文字背景轮播' className='card-wrap' >
                    <Carousel>
                        <div><h3>Ant Motion Banner - React</h3></div>
                        <div><h3>Ant Motion Banner - Vue</h3></div>
                        <div><h3>Ant Motion Banner - Angular</h3></div>
                    </Carousel>
                </Card>
                <Card title='文字背景自动轮播' className='card-wrap' >
                    <Carousel autoplay>
                        <div><h3>Ant Motion Banner - React</h3></div>
                        <div><h3>Ant Motion Banner - Vue</h3></div>
                        <div><h3>Ant Motion Banner - Angular</h3></div>
                    </Carousel>
                </Card>
                <Card title='文字背景自动轮播 + 动画' className='card-wrap' >
                    <Carousel autoplay effect='fade' >
                        <div><h3>Ant Motion Banner - React</h3></div>
                        <div><h3>Ant Motion Banner - Vue</h3></div>
                        <div><h3>Ant Motion Banner - Angular</h3></div>
                    </Carousel>
                </Card>
                <Card title='图片轮播' className='card-wrap' >
                    <Carousel autoplay effect='fade' >
                        <div><img /></div>
                        <div><img /></div>
                        <div><img /></div>
                    </Carousel>
                </Card>
            </div>
        )
    }
}
```

## 第6章 表单使用

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/29.png)

### 6-1登录表单讲解(上)

```jsx
import React from 'react'
import { Card, Form, Input, Button } from 'antd';

const FormItem = Form.Item

class FormLogin extends React.Component {
    render() {
        const { getFieldDecorator } = this.props.form
        return (
            <div>
                <Card title='登陆行内表单' >
                    <Form layout='inline' >
                        <FormItem>
                            <Input placeholder='请输入用户名' />
                        </FormItem>
                        <FormItem>
                            <Input placeholder='请输入密码' />
                        </FormItem>
                        <FormItem>
                            <Button type='primary' >登陆</Button>
                        </FormItem>
                    </Form>
                </Card>
                <Card title='登陆水平表单' style={{marginTop: 10}} >
                    <Form style={{width: 300}} >
                        <FormItem>
                            {
                                getFieldDecorator('username', {
                                    initialValue: 'Jack',
                                    rules: []
                                })(<Input placeholder='请输入用户名' />)
                            }
                        </FormItem>
                        <FormItem>
                            {
                                getFieldDecorator('userPwd', {
                                    initialValue: '123456',
                                    rules: []
                                })(<Input placeholder='请输入密码' />)
                            }
                        </FormItem>
                        <FormItem>
                            <Button type='primary' >登陆</Button>
                        </FormItem>
                    </Form>
                </Card>
            </div>
        )
    }
}

export default Form.create()(FormLogin)
```

如果

```jsx
{
    getFieldDecorator('userPwd', {
        initialValue: '123456',
        rules: []
    })(<Input placeholder='请输入密码' />)
}
```

中的`userPwd`改成`username`，那么用户名和密码两个input可以实现类似于vue.js的数据双向绑定的功能。

### 6-2登录表单讲解(下)

```jsx
import React from 'react'
import { Card, Form, Input, Button, message, Icon, Checkbox } from 'antd';

const FormItem = Form.Item

class FormLogin extends React.Component {
    handleSubmit = () => {
        let userInfo = this.props.form.getFieldsValue()
        this.props.form.validateFields((err, values) => {
            if (!err) {
                message.success(`${userInfo.userName} 恭喜你， 您通过本次表单学习，当前密码为：${userInfo.userPwd}`)
            }
        })
    }

    render() {
        const { getFieldDecorator } = this.props.form
        return (
            <div>
                <Card title='登陆行内表单' >
                    <Form layout='inline' >
                        <FormItem>
                            <Input placeholder='请输入用户名' />
                        </FormItem>
                        <FormItem>
                            <Input placeholder='请输入密码' />
                        </FormItem>
                        <FormItem>
                            <Button type='primary' >登陆</Button>
                        </FormItem>
                    </Form>
                </Card>
                <Card title='登陆水平表单' style={{marginTop: 10}} >
                    <Form style={{width: 300}} >
                        <FormItem>
                            {
                                getFieldDecorator('userName', {
                                    initialValue: '',
                                    rules: [
                                        {
                                            required: true,
                                            message: '用户名不能为空'
                                        },
                                        {
                                            min: 5,
                                            max: 10,
                                            message: '长度不在范围内'
                                        },
                                        {
                                            pattern: new RegExp('^\\w+$', 'g'),
                                            message: '用户名必须为数字或英文字母'
                                        }
                                    ]
                                })(<Input prefix={<Icon type='user' />} placeholder='请输入用户名' />)
                            }
                        </FormItem>
                        <FormItem>
                            {
                                getFieldDecorator('userPwd', {
                                    initialValue: '',
                                    rules: []
                                })(<Input prefix={<Icon type='lock' />} placeholder='请输入密码' />)
                            }
                        </FormItem>
                        <FormItem>
                            {
                                getFieldDecorator('remember', {
                                    valuePropName: 'checked',
                                    initialValue: true,
                                    rules: []
                                })(
                                    <Checkbox>记住密码</Checkbox>
                                )
                            }
                            <a href='#' style={{float: 'right'}} >忘记密码</a>
                        </FormItem>
                        <FormItem>
                            <Button type='primary' onClick={this.handleSubmit} >登陆</Button>
                        </FormItem>
                    </Form>
                </Card>
            </div>
        )
    }
}

export default Form.create()(FormLogin)
```

## 第7章基础表格、高级表格使用

### 7-1基础表格讲解

表头至少得有`title`和`dataIndex`。

```jsx
import React from 'react'
import { Card, Table } from 'antd';

export default class BasicTable extends React.Component {
    state = {}
    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        this.setState({
            dataSource
        })
    }
    

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex'
            },
            {
                title: '状态',
                dataIndex: 'state'
            },
            {
                title: '爱好',
                dataIndex: 'interest'
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]
        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />

                </Card>
            </div>
        )
    }
}
```

其中：

```jsx
pagination={false}
```

代表不需要分页。

注意：

```jsx
const dataSource
```

如果我们定义的变量名字不是`dataSource`而是其他的，例如`data`，那么我们在`setState`的时候需要这样写：

```jsx
this.setState({
    dataSource: data
})
```

### 7-2项目工程化之表格动态渲染(1)

![](http://oklbfi1yj.bkt.clouddn.com/React%E5%85%A8%E5%AE%B6%E6%A1%B6+AntD%20%E5%85%B1%E4%BA%AB%E5%8D%95%E8%BD%A6%E5%90%8E%E5%8F%B0%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F%E5%BC%80%E5%8F%91/30.png)

我们使用`easy mock`这个网站来Mock数据。（学习一下mock.js规范，因为`easy mock`这个网站遵循这个规范）

我们使用的mock数据如下：

```
{
  "code": 0,
  "msg": '',
  "result|10": [{
    "id|+1": 1,
    userName: '@cname',
    "sex|1-2": 1,
    "state|1-5": 1,
    "interest|1-5": 1,
    birthday: '2000-01-01',
    address: '江西省',
    time: '09:00'
  }]
}
```

我们通过axios来获取数据：

```jsx
import React from 'react'
import { Card, Table } from 'antd';
import axios from 'axios'

export default class BasicTable extends React.Component {
    state = {
        dataSource2: []
    }
    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        this.setState({
            dataSource
        })
        this.request()
    }

    // 动态获取mock数据
    request = () => {
        let baseUrl = 'https://www.easy-mock.com/mock/5b2e3cc8f3689f014644b519/imoocmockapi'
        axios.get(baseUrl + '/table/list').then((res) => {
            if (res.status == '200' && res.data.code == 0) {
                this.setState({
                    dataSource2: res.data.result
                })
            }
        })
    }
    

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex'
            },
            {
                title: '状态',
                dataIndex: 'state'
            },
            {
                title: '爱好',
                dataIndex: 'interest'
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]
        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />
                </Card>
                <Card title='动态数据渲染表格' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
            </div>
        )
    }
}
```

### 7-3项目工程化之表格动态渲染(2)

#### 封装axios插件

```jsx
import JsonP from 'jsonp'
import axios from 'axios'
import { Modal } from 'antd';

export default class Axios {
    static jsonp(options) {
        return new Promise((resolve, reject) => {
            JsonP(options.url, {
                param: 'callback'
            }, function(err, response) {
                if (response.status == 'success') {
                    resolve(response)
                }
                else {
                    reject(response.message)
                }
            })
        })
    }

    static ajax(options) {
        let baseApi = 'https://www.easy-mock.com/mock/5b2e3cc8f3689f014644b519/imoocmockapi'

        return new Promise((resolve, reject) => {
            axios({
                url: options.url,
                method: 'get',
                baseURL: baseApi,
                timeout: 5000,
                params: (options.data && options.data.params) || ''
            }).then((response) => {
                if (response.status == '200') {
                    let res = response.data
                    if (res.code == '0') {
                        resolve(res)
                    }
                    else {
                        Modal.info({
                            title: '提示',
                            content: res.meg
                        })
                    }
                }
                else {
                    reject(response.data)
                }
            })
        })
    }
}
```

#### 使用这个封装好的类

```jsx
import React from 'react'
import { Card, Table } from 'antd';
import Axios from './../../axios/index'

export default class BasicTable extends React.Component {
    state = {
        dataSource2: []
    }
    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        this.setState({
            dataSource
        })
        this.request()
    }

    // 动态获取mock数据
    request = () => {
        Axios.ajax({
            url: '/table/list',
            data: {
                params: {
                    page: 1
                }
            }
        }).then((res) => {
            if (res.code == 0) {
                this.setState({
                    dataSource2: res.result
                })
            }
        })
    }
    

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex'
            },
            {
                title: '状态',
                dataIndex: 'state'
            },
            {
                title: '爱好',
                dataIndex: 'interest'
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]
        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />
                </Card>
                <Card title='动态数据渲染表格' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
            </div>
        )
    }
}
```

### 7-4项目工程化之表格动态渲染(3)

```jsx
import React from 'react'
import { Card, Table } from 'antd';
import Axios from './../../axios/index'

export default class BasicTable extends React.Component {
    state = {
        dataSource2: []
    }
    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        this.setState({
            dataSource
        })
        this.request()
    }

    // 动态获取mock数据
    request = () => {
        Axios.ajax({
            url: '/table/list',
            data: {
                params: {
                    page: 1
                }
            }
        }).then((res) => {
            if (res.code == 0) {
                this.setState({
                    dataSource2: res.result
                })
            }
        })
    }
    

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex',
                render(sex) {
                    return sex == 1 ? '男' : '女'
                }
            },
            {
                title: '状态',
                dataIndex: 'state',
                render(state) {
                    let config = {
                        '1': '咸鱼一条',
                        '2': '风华浪子',
                        '3': '北大才子',
                        '4': '百度FE',
                        '5': '创业者'
                    }

                    return config[state]
                }
            },
            {
                title: '爱好',
                dataIndex: 'interest',
                render(interest) {
                    let config = {
                        '1': '游泳',
                        '2': '篮球',
                        '3': '乒乓球',
                        '4': '足球',
                    }

                    return config[interest]
                }
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]
        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />
                </Card>
                <Card title='动态数据渲染表格' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
            </div>
        )
    }
}
```

### 7-5表格嵌套单选按钮讲解

表格中的每条记录都需要一个key。

`rowSelection`设置表格记录是单选还是多选。并且要指定`selectedRowKeys`。

```jsx
import React from 'react'
import { Card, Table, Modal } from 'antd';
import Axios from './../../axios/index'

export default class BasicTable extends React.Component {
    state = {
        dataSource2: []
    }
    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        dataSource.map((item, index) => {
            item.key = index
        })
        this.setState({
            dataSource
        })
        this.request()
    }

    // 动态获取mock数据
    request = () => {
        Axios.ajax({
            url: '/table/list',
            data: {
                params: {
                    page: 1
                }
            }
        }).then((res) => {
            if (res.code == 0) {
                res.result.map((item, index) => {
                    item.key = index
                })

                this.setState({
                    dataSource2: res.result
                })
            }
        })
    }
    
    onRowClick = (record, index) => {
        let selectKey = [index]
        // Modal.info({
        //     title: '信息',
        //     content: `用户名: ${record.userName}, 用户爱好: ${record.interest}`
        // })
        this.setState({
            selectedRowKeys: selectKey,
            selectedItem: record
        })
    }

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex',
                render(sex) {
                    return sex == 1 ? '男' : '女'
                }
            },
            {
                title: '状态',
                dataIndex: 'state',
                render(state) {
                    let config = {
                        '1': '咸鱼一条',
                        '2': '风华浪子',
                        '3': '北大才子',
                        '4': '百度FE',
                        '5': '创业者'
                    }

                    return config[state]
                }
            },
            {
                title: '爱好',
                dataIndex: 'interest',
                render(interest) {
                    let config = {
                        '1': '游泳',
                        '2': '篮球',
                        '3': '乒乓球',
                        '4': '足球',
                    }

                    return config[interest]
                }
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]

        const selectedRowKeys = this.state.selectedRowKeys
        const rowSelection = {
            type: 'radio',
            selectedRowKeys
        }
        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />
                </Card>
                <Card title='动态数据渲染表格--Mock' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
                <Card title='Mock--单选' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        rowSelection={rowSelection}
                        onRow={(record, index) => {
                            return {
                                onClick: () => {
                                    this.onRowClick(record, index)
                                } // 点击行
                            }
                        }}
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
            </div>
        )
    }
}
```

### 7-6表格嵌套多选按钮

```jsx
import React from 'react'
import { Card, Table, Modal, Button, message } from 'antd';
import Axios from './../../axios/index'

export default class BasicTable extends React.Component {
    state = {
        dataSource2: []
    }
    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        dataSource.map((item, index) => {
            item.key = index
        })
        this.setState({
            dataSource
        })
        this.request()
    }

    // 动态获取mock数据
    request = () => {
        Axios.ajax({
            url: '/table/list',
            data: {
                params: {
                    page: 1
                }
            }
        }).then((res) => {
            if (res.code == 0) {
                res.result.map((item, index) => {
                    item.key = index
                })

                this.setState({
                    dataSource2: res.result,
                    selectedRowKeys: [],
                    selectedRows: null
                })
            }
        })
    }
    
    onRowClick = (record, index) => {
        let selectKey = [index]
        // Modal.info({
        //     title: '信息',
        //     content: `用户名: ${record.userName}, 用户爱好: ${record.interest}`
        // })
        this.setState({
            selectedRowKeys: selectKey,
            selectedItem: record
        })
    }

    handleDelete = () => {
        let rows = this.state.selectedRows
        let ids = []
        rows.map((item) => {
            ids.push(item.id)
        })
        Modal.confirm({
            title: '删除提示',
            content: `您确定要删除这些数据吗? ${ids.join(',')}`,
            onOk: () => {
                message.success('删除成功')
                this.request()
            }
        })
    }

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex',
                render(sex) {
                    return sex == 1 ? '男' : '女'
                }
            },
            {
                title: '状态',
                dataIndex: 'state',
                render(state) {
                    let config = {
                        '1': '咸鱼一条',
                        '2': '风华浪子',
                        '3': '北大才子',
                        '4': '百度FE',
                        '5': '创业者'
                    }

                    return config[state]
                }
            },
            {
                title: '爱好',
                dataIndex: 'interest',
                render(interest) {
                    let config = {
                        '1': '游泳',
                        '2': '篮球',
                        '3': '乒乓球',
                        '4': '足球',
                    }

                    return config[interest]
                }
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]

        const selectedRowKeys = this.state.selectedRowKeys
        const rowSelection = {
            type: 'radio',
            selectedRowKeys
        }

        const rowCheckSelection = {
            type: 'checkbox',
            selectedRowKeys,
            onChange: (selectedRowKeys, selectedRows) => {
                this.setState({
                    selectedRowKeys,
                    selectedRows
                })
            }
        }

        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />
                </Card>
                <Card title='动态数据渲染表格--Mock' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
                <Card title='Mock--单选' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        rowSelection={rowSelection}
                        onRow={(record, index) => {
                            return {
                                onClick: () => {
                                    this.onRowClick(record, index)
                                } // 点击行
                            }
                        }}
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
                <Card title='Mock--多选' style={{margin: '10px 0'}} >
                    <div style={{marginBottom: 10}} >
                        <Button onClick={this.handleDelete} >删除</Button>
                    </div>
                    <Table
                        bordered
                        rowSelection={rowCheckSelection}
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
            </div>
        )
    }
}
```

### 7-7表格分页

mock的数据：

```
{
  "code": 0,
  "msg": '',
  "result": {
    "list|5": [{
      "id|+1": 1,
      userName: '@cname',
      "sex|1-2": 1,
      "state|1-5": 1,
      "interest|1-5": 1,
      birthday: '2000-01-01',
      address: '江西省',
      time: '09:00'
    }],
    page: 1,
    page_size: 10,
    total: 100
  }
}
```

封装分页组件：

```jsx
import { Pagination } from "antd";

export default {
    formateDate(time) {
        if (!time) {
            return ''
        }
        else {
            let date = new Date(time)
            return date.getFullYear() + '-' + (date.getMonth() + 1) + '-' + date.getDate() + ' ' + date.getHours() + ':' + date.getMinutes() + ':' + date.getSeconds()
        }
    },

    pagination(data, callback) {
        let page = {
            onChange: (current) => {
                callback(current)
            },
            current: data.result.page,
            pageSize: data.result.page_size,
            total: data.result.total,
            showTotal: () => {
                return `共${data.result.total}条`
            },
            showQuickJumper: true
        }

        return page
    }
}
```

```jsx
import React from 'react'
import { Card, Table, Modal, Button, message } from 'antd';
import Axios from './../../axios/index'
import Utils from './../../utils/utils';

export default class BasicTable extends React.Component {
    state = {
        dataSource2: []
    }

    params = {
        page: 1
    }

    componentDidMount() {
        const dataSource = [
            {
                id: '0',
                userName: 'Jack',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '1',
                userName: 'Tom',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            },
            {
                id: '2',
                userName: 'Lily',
                sex: '1',
                state: '1',
                interest: '1',
                birthday: '2000-01-01',
                address: '江西省',
                time: '09:00'
            }
        ]
        dataSource.map((item, index) => {
            item.key = index
        })
        this.setState({
            dataSource
        })
        this.request()
    }

    // 动态获取mock数据
    request = () => {
        let _this = this
        Axios.ajax({
            url: '/table/list',
            data: {
                params: {
                    page: this.params.page
                }
            }
        }).then((res) => {
            if (res.code == 0) {
                res.result.list.map((item, index) => {
                    item.key = index
                })

                this.setState({
                    dataSource2: res.result.list,
                    selectedRowKeys: [],
                    selectedRows: null,
                    pagination: Utils.pagination(res, (current) => {
                        _this.params.page = current
                        this.request()
                    })
                })
            }
        })
    }
    
    onRowClick = (record, index) => {
        let selectKey = [index]
        // Modal.info({
        //     title: '信息',
        //     content: `用户名: ${record.userName}, 用户爱好: ${record.interest}`
        // })
        this.setState({
            selectedRowKeys: selectKey,
            selectedItem: record
        })
    }

    handleDelete = () => {
        let rows = this.state.selectedRows
        let ids = []
        rows.map((item) => {
            ids.push(item.id)
        })
        Modal.confirm({
            title: '删除提示',
            content: `您确定要删除这些数据吗? ${ids.join(',')}`,
            onOk: () => {
                message.success('删除成功')
                this.request()
            }
        })
    }

    render() {
        const colums = [ // 因为这些数据是不会变的，所以我们放在render函数里面。如果放在外面的话，需要通过this.state来获取，比较麻烦一点
            {
                title: 'id',
                dataIndex: 'id'
            },
            {
                title: '用户名',
                dataIndex: 'userName'
            },
            {
                title: '性别',
                dataIndex: 'sex',
                render(sex) {
                    return sex == 1 ? '男' : '女'
                }
            },
            {
                title: '状态',
                dataIndex: 'state',
                render(state) {
                    let config = {
                        '1': '咸鱼一条',
                        '2': '风华浪子',
                        '3': '北大才子',
                        '4': '百度FE',
                        '5': '创业者'
                    }

                    return config[state]
                }
            },
            {
                title: '爱好',
                dataIndex: 'interest',
                render(interest) {
                    let config = {
                        '1': '游泳',
                        '2': '篮球',
                        '3': '乒乓球',
                        '4': '足球',
                    }

                    return config[interest]
                }
            },
            {
                title: '生日',
                dataIndex: 'birthday'
            },
            {
                title: '地址',
                dataIndex: 'address'
            },
            {
                title: '早起时间',
                dataIndex: 'time'
            }
        ]

        const selectedRowKeys = this.state.selectedRowKeys
        const rowSelection = {
            type: 'radio',
            selectedRowKeys
        }

        const rowCheckSelection = {
            type: 'checkbox',
            selectedRowKeys,
            onChange: (selectedRowKeys, selectedRows) => {
                this.setState({
                    selectedRowKeys,
                    selectedRows
                })
            }
        }

        return (
            <div>
                <Card title='基础表格' >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource}
                        pagination={false}
                    />
                </Card>
                <Card title='动态数据渲染表格--Mock' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
                <Card title='Mock--单选' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        rowSelection={rowSelection}
                        onRow={(record, index) => {
                            return {
                                onClick: () => {
                                    this.onRowClick(record, index)
                                } // 点击行
                            }
                        }}
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
                <Card title='Mock--多选' style={{margin: '10px 0'}} >
                    <div style={{marginBottom: 10}} >
                        <Button onClick={this.handleDelete} >删除</Button>
                    </div>
                    <Table
                        bordered
                        rowSelection={rowCheckSelection}
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={false}
                    />
                </Card>
                <Card title='Mock--表格分页' style={{margin: '10px 0'}} >
                    <Table
                        bordered
                        columns={colums}
                        dataSource={this.state.dataSource2}
                        pagination={this.state.pagination}
                    />
                </Card>
            </div>
        )
    }
}
```





















