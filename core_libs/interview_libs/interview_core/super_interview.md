
# 超级面试宝典🌻
>面试造火箭 了解一下怎么造火箭也挺好的🤓

## 一些说明
- 加油/坚持/效率/输出

## 导航大纲
- [html小分队🌳](#html小分队🌳)
  - [页面导入样式的时候使用link和import有什么区别](#页面导入样式的时候使用link和import有什么区别)
  - [在页面上隐藏元素的方法有哪些](#在页面上隐藏元素的方法有哪些)
  - [页面渲染html的过程](#页面渲染html的过程)
  - [如何让a标签鼠标悬停变色](#如何让a标签鼠标悬停变色)
  - [元素的alt和title有什么异同](#元素的alt和title有什么异同)
- [css小分队🍉](#css小分队🍉)
  - [如何取消li的默认样式](#如何取消li的默认样式)
  - [清除浮动的方式及优缺点](#清除浮动的方式及优缺点)
  - [说一下盒子模型的理解](#说一下盒子模型的理解)
  - [使用flex实现一个上下左右居中的布局](#使用flex实现一个上下左右居中的布局)
  - [css有哪些选择器](#css有哪些选择器)
  - [css样式的优先级](#css样式的优先级)
  - [常见的自适应布局](#常见的自适应布局)
  - [css常用的布局方式有哪些](#css常用的布局方式有哪些)
  - [style标签写在body前和body后的区别是什么](#style标签写在body前和body后的区别是什么)
  - [简述下你理解的优雅降级和渐进增强](#简述下你理解的优雅降级和渐进增强)
  - [css可以继承的属性](#css可以继承的属性)
- [js小分队🐎](#js小分队🐎)
  - [写一个获取数组的最大最小值的方法](#写一个获取数组的最大最小值的方法)
  - [如何删除对象的a属性](#如何删除对象的a属性)
  - [说一下常用的数组方法](#说一下常用的数组方法)
  - [typeof的返回值](#typeof的返回值)
  - [说一下null和undefined的区别](#说一下null和undefined的区别)
  - [说一下js的数据类型](#说一下js的数据类型)
  - [浅拷贝和深拷贝的区别及如何实现深拷贝](#浅拷贝和深拷贝的区别及如何实现深拷贝)
  - [请用一行代码实现深拷贝](#请用一行代码实现深拷贝)
  - [适合用事件委托的事件有哪些](#适合用事件委托的事件有哪些)
  - [什么是事件委托](#什么是事件委托)
  - [什么是冒泡事件](#什么是冒泡事件)
  - [如何取消默认事件](#如何取消默认事件)
  - [如何防止冒泡和捕获事件](#如何防止冒泡和捕获事件)
  - [说一下js有哪些内置对象](#说一下js有哪些内置对象)
  - [说一下原型对象](#说一下原型对象)
  - [说一下原型链](#说一下原型链)
  - [说一下作用域链](#说一下作用域链)
  - [toString和valueOf的区别](#toString和valueOf的区别)
  - [Object是在堆还是栈里面](#Object是在堆还是栈里面)
  - [垃圾回收的两种方法](#垃圾回收的两种方法)
  - [说一下闭包](#说一下闭包)
- [vue小分队🍖](#vue小分队🍖)
  - [v-show和v-if的区别](#v-show和v-if的区别)
  - [为什么要替换defineProperty](#为什么要替换defineProperty)
  - [vue3和vue2的区别](#vue3和vue2的区别)
  - [虚拟dom的优劣](#虚拟dom的优劣)
  - [虚拟dom的实现原理](#虚拟dom的实现原理)
  - [说一下双向绑定的原理](#说一下双向绑定的原理)
- [小程序小分队👻](#小程序小分队👻)
  - [说一下小程序的支付流程](#说一下小程序的支付流程)
  - [小程序怎么实现双向绑定](#小程序怎么实现双向绑定)
  - [bindtap和catchtap的区别](#bindtap和catchtap的区别)
  - [小程序的本地存储和web的区别](#小程序的本地存储和web的区别)
  - [setData和data的区别](#setData和data的区别)
  - [open-type的作用](#open-type的作用)
  - [如何获取用户信息](#如何获取用户信息)
  - [如何授权登录](#如何授权登录)
- [http协议小分队🌐](#http协议小分队🌐)
  - [协议和域名不同的情况是否同域](#协议和域名不同的情况是否同域)
  - [浏览器输入url后发生了什么](#浏览器输入url后发生了什么)
  - [说一下跨域及如何解决跨域](#说一下跨域及如何解决跨域)
  - [说一下你知道的状态码](#说一下你知道的状态码)
- [其他小分队🔫](#其他小分队🔫)
  - [常用的五个网站](#常用的五个网站)
- [一些其他的私有数据😈](https://github.com/techpang666/cloud_office/blob/master/markdown/interview_libs/setout/interview_essay.md)

---
## html小分队🌳

### 页面导入样式的时候使用link和import有什么区别

1. link是HTML标签，@import是css提供的。
2. link引入的样式页面加载时同时加载，@import引入的样式需等页面加载完成后再加载。
3. link没有兼容性问题，@import不兼容**ie5**以下。
4. link可以通过js操作DOM动态改变样式，而@import不可以。

### 在页面上隐藏元素的方法有哪些

- display: none
- opacity: 0
- visibility: hidden
- z-index: -999
- transform: scale(0)
- margin-left: -100%
- position: relative; left: -100%
- width: 0; height: 0;

### 页面渲染html的过程

1. 解析HTML文件，创建DOM树
2. 解析CSS,形成CSS对象模型
3. 将CSS与DOM合并，构建渲染树
4. 布局和绘制

### 如何让a标签鼠标悬停变色

```css
a:hover {
  color: pink;
}
```

### 元素的alt和title有什么异同

alt作为图片的**替代文字**出现，title作为图片的解释文字出现

---
## css小分队🍉

### 如何取消li的默认样式

```css
.demo {
  list-style: none;
}
```

### 清除浮动的方式及优缺点

- 在浮动元素后使用一个带clear属性的空元素(引入了冗余的元素)
- 用overflow: hidden清除浮动(有可能造成溢出元素不可见 影响展示效果)
- 用after伪元素清除浮动(bootstrap框架采用的清除浮动的方法)

### 说一下盒子模型的理解

css有两种盒子模型 分别是标准盒子模型和怪异盒子模型

- 标准盒子模型的宽度是content
- 怪异盒子模型的宽度是content + border + padding

```css
.demo {
  /* 标准盒子模型 */
  box-sizing: content-box;
  /* 怪异盒子模型 */
  box-sizing: border-box;
}
```

### 使用flex实现一个上下左右居中的布局

```css
.demo {
	display: flex;
	justify-content: center;
	align-items: center;
}
```

### css有哪些选择器

- 通配符
- id
- class
- 标签
- 后代选择器
- 子选择器
- 兄弟选择器
- 属性选择器
- 伪类选择器
- 伪元素选择器

### css样式的优先级

!important > 内联样式 > ID 选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 标签选择器 = 伪元素选择器 > 通配符选择器 > 继承 > 浏览器默认属性

### 常见的自适应布局

- flex布局
- 圣杯布局
- 双飞翼布局

**圣杯/双飞翼都是用float实现的**

### css常用的布局方式有哪些

1. **流式布局** 最基本的布局，就是顺着html像流水一样流下来
2. **绝对定位** 利用position: absolute进行绝对定位的布局
3. **float布局** 最初用来解决多栏布局的问题。比如圣杯/双飞翼的布局都可以用float来实现
4. **珊格布局** bootstrap用的布局，把页面分为24份，通过row和col进行布局
5. **flex布局** css3的布局可以非常灵活地进行布局和排版
6. **grid布局** 网格布局

### style标签写在body前和body后的区别是什么

放在body前会跟HTML同时渲染

放在body后，浏览器会先渲染HTML，再渲染CSS

则会导致一开始出现一个没有样式的界面，再跳到有样式的界面

### 简述下你理解的优雅降级和渐进增强

- **优雅降级** 先做好一个完善的具备完整体验的版本，再向下做兼容
- **渐进增强** 先做好一个可以基本正常使用的版本，再慢慢丰富体验和内容

### css可以继承的属性

- color
- font-size
- font-weight
- font-style
- font-family

---
## js小分队🐎

### 写一个获取数组的最大最小值的方法

```js
let demo = [25, 62, 91, 78, 34, 62];
let max_res = Math.max.apply(this, demo);
let min_res = Math.min.apply(this, demo);
console.log(max_res); /* 91 */
console.log(min_res); /* 25 */
// 用this和Array都是全等的
console.log(Math.min.apply(this, demo) === Math.min.apply(Array, demo)); /* true */
```

### 如何删除对象的a属性

```js
let obj = { a: 0, b: 1 };
delete obj.a;
console.log(obj);
```

### 说一下常用的数组方法

1. push
2. map
3. sort
4. splice
5. forEach

### typeof的返回值

一共七种
1. number
2. string
3. boolean
4. undefined
5. symbol
6. object
7. function

一些细节
- null也会返回object(因为null是空对象指针)
- array需要通过toString.call()判断 typeof不能判断数组
- symbol为符号

### 说一下null和undefined的区别

null只有一个值 就是null 它表示空值

null的典型用法
1. 作为函数的参数，表示该函数的参数不是对象
2. 作为对象原型链的终点

undefined也是只有一个值 就是undefined 它表示已经定义但未赋值

undefined的典型用法
1. 调用函数时，应该提供的参数没有提供，该参数等于undefined
2. 变量被声明了，但没有赋值时，就等于undefined
3. 对象没有赋值的属性，该属性的值为undefined
4. 函数没有返回值时，默认返回undefined

### 说一下js的数据类型

六种基本类型 三种引用类型 其中symbol属于es6的

基本类型
1. number
2. string
3. boolean
4. undefined
5. null
6. symbol

引用类型
1. object
2. function
3. array

### 浅拷贝和深拷贝的区别及如何实现深拷贝

区别在于是否开辟了一个新的地址

**公用一个地址就是浅拷贝** 否则就是深拷贝

可以通过浅拷贝+递归实现深拷贝

浅拷贝时**判断属性值是否是对象**

如果是对象就进行递归操作

这样就实现了深拷贝

### 请用一行代码实现深拷贝

```js
let demo = JSON.parse(JSON.stringify(obj))
```

### 适合用事件委托的事件有哪些

- click
- mousedown
- mouseup
- keydown
- keyup
- keypress

### 什么是事件委托

事件委托是利用事件的冒泡原理来实现的

优点
- 减少事件注册，节省内存
- 简化了dom节点更新时，相应事件的更新

缺点
- 事件委托基于冒泡，对于**不冒泡的事件**不支持
- 层级过多，冒泡过程中，**可能会被某层阻止掉**

### 什么是冒泡事件

在一个按钮中绑定一个click事件 它会依次在父元素中被触发

### 如何取消默认事件

通过e.preventDefault()

### 如何防止冒泡和捕获事件

通过e.stopPropagation()

### 说一下js有哪些内置对象

- 数值对象Number
- 字符串对象String
- 布尔对象Boolean
- 时间对象Date
- 数学对象Math
- 错误对象Error
- 数组对象Array
- 基础对象Object
- 函数对象Function
- 函数参数集合arguments

### 说一下原型对象

每个函数都有一个prototype属性 指向它的原型对象

基于构造函数创建的实例 可以访问它的原型对象上的方法

比如toString是Object原型对象上的方法 可以被任何实例作为自己的方法进行调用

实例在调用属性和方法的时候 优先调用自己的

如果自己没有就找原型的 原型没有就找原型的原型 直到原型顶端Object.protototype(原型链的顶端)

hasOwnProperty就是用来判断某个属性是不是自己的

### 说一下原型链

每个对象都有一个__proto__属性 指向它的构造函数的原型

对象可以通过__proto__属性和构造函数的原型对象进行连接

然后构造函数的原型对象也有__proto__属性

这样就形成了链式结构 我们称之为原型链

### 说一下作用域链

函数内部可以访问到外部变量

外部函数可以访问到全局变量

这样形成的变量作用域链式结构 被称为作用域链

### toString和valueOf的区别

对象的两个方法 Object.protototype

toString() 返回对象的字符串表示
valueOf() 返回对象的字符串/数值或布尔值表示(其实就是返回自身)

toString()在对象的时候 就变成"[object Object]"

表示数组的时候 就变成数组内容以逗号连接的字符串 相当于Array.join(',')

valueOf的优先级比toString高

### Object是在堆还是栈里面

**堆里面**

栈内存主要用于存储各种基本类型的变量 比如Boolean/Number/String/Undefined/Null

堆内存主要负责像对象Object这种变量类型的存储

### 垃圾回收的两种方法

**垃圾回收**

核心思想就是如何判断内存是否已经不再会被使用了

如果是 就视为垃圾释放掉

- 引用计数法
- 标记清除法

**引用计数法**

定义“内存不再使用”的标准很简单

就是看一个对象是否有指向它的引用

如果没有任何变量指向它了 说明该对象已经不再需要了

**标记清除法**

标记清除算法将“不再使用的对象”定义为“无法达到的对象”

### 说一下闭包

闭包是一个函数嵌套另一个函数

优点可以防止全局变量污染

缺点会造成内存泄漏

闭包最大的作用就是用来变量私有

---
## vue小分队🍖

### v-show和v-if的区别

两者都是用来显示隐藏元素的

不同的是
1. v-if是通过销毁和重建DOM让元素显示隐藏的
2. v-show是通过修改display属性让元素显示隐藏的
3. v-if有更高的切换开销 而v-show是有更高的首次渲染开销

### 为什么要替换defineProperty

defineProperty只能响应**首次渲染时候的属性**

Proxy需要的是**整体** 不需要关心里面有什么属性

**而且Proxy的配置项有13种** 可以做更细致的事情 这是defineProperty做不到的

### vue3和vue2的区别

1. setup代替了之前的beforeCreate和created
2. proxy代替Object.defineProperty(vue2的双向绑定的核心)
3. diff算法的提升
4. typeScript的支持
5. 打包体积的优化
6. 使用自己的构建工具vite

### 虚拟dom的优劣

1. 保证性能下限
2. 无需手动操作DOM
3. 跨平台
4. 无法进行极致优化

**保证性能下限** 虚拟DOM可以经过diff找出最小差异,然后批量进行patch,这种操作虽然比不上手动优化,但是比起粗暴的DOM操作性能要好很多,因此虚拟DOM可以保证性能下限

**无需手动操作DOM** 虚拟DOM的diff和patch都是在**一次更新中自动进行**的,我们无需手动操作DOM,极大提高开发效率

**跨平台** 虚拟DOM本质上是JavaScript对象,而DOM与平台强相关,相比之下虚拟DOM可以进行更方便地跨平台操作,例如服务器渲染、移动端开发等等

**无法进行极致优化** 在一些性能要求极高的应用中虚拟DOM无法进行针对性的极致优化

### 虚拟dom的实现原理

1. 虚拟DOM本质上是JavaScript对象,是对真实DOM的抽象
2. 状态变更时，记录新树和旧树的差异
3. 最后把差异更新到真正的dom中

### 说一下双向绑定的原理

利用Object.defineProperty劫持对象的访问器

当属性值发生变化的时候 我们获取变化进行后续的操作

vue3通过proxy进行类似的操作

---
## 小程序小分队👻

### 说一下小程序的支付流程

1. 获取用户的token
2. 创建订单
3. 获取预支付参数
4. 发起微信支付

用户的token需要五个参数

其中code通过wx.login()获取 其他通过wx.getUserProfile()获取

然后就可以创建订单了 订单需要请求头和请求体参数
- 请求头就需要token
- 请求体是用户的商品列表/总价/收获地址等信息

这时候就可以通过订单编号获取预支付参数(五个参数)

然后通过wx.requestPayment()传入预支付参数 就可以发起微信支付了

### 小程序怎么实现双向绑定

**通过bindinput属性**

小程序是单向数据流 我们可以通过bindinput属性来实现双向数据绑定

1. 在bindinput属性中定义个方法
2. 在data中定义个message
3. 通过e.detail.value获取用户输入的值
4. 然后通过this.setData()更新数据

```html
<text>这是用来显示文本的：{{message}}</text>
<input bindinput="getMessage" placeholder="这是输入框" />
```

```js
  data: {
    message: ''
  },
  getMessage(e) {
    let message = e.detail.value
    this.setData({
      message
    })
  },
```

### bindtap和catchtap的区别

bindtap不能阻止事件冒泡 catchtap可以

### 小程序的本地存储和web的区别

- 使用的方法不同
- 有没有类型转换

小程序是通过这两个方法进行缓存获取数据的
- wx.setStorageSync()
- wx.getStorageSync()

web是通过这两个方法
- localStorage.setItem()
- localStorage.getItem()

web不管存入什么类型的数据都会通过toString()变成字符串存储

小程序不存在什么类型转换 存放什么类型的数据 获取的时候就是什么类型的数据

### setData和data的区别

this.setData()用于将数据从逻辑层发送到视图层 同时改变对应的this.data的值

用this.data会造成页面内容不更新的问题

### open-type的作用

用于获取手机号/客服/用户信息等等

### 如何获取用户信息

通过wx.getUserProfile()获取

原来是通过open-type="getUserInfo" 然后数据在e.detail里面

### 如何授权登录

通过code和第三方服务器进行注册登录

code通过wx.login()获取

用户信息通过wx.getUserProfile()获取 数据在res里面

然后通过wx.setStorageSync()缓存用户信息 wx.getStorageSync()进行获取用户信息 this.setData()更新数据

---
## http协议小分队🌐

### 协议和域名不同的情况是否同域

**不同的**

同域的要求是 请求地址中的协议/域名及端口号都相同

只要有一个不相同就是跨域

### 浏览器输入url后发生了什么

1. DNS解析
2. TCP连接
3. 发送HTTP请求
4. 服务器处理请求 并返回HTTP报文
5. 浏览器解析渲染页面
6. 连接结束

### 说一下跨域及如何解决跨域

跨域是浏览器的同源策略造成的

有三种解决方案
- cors
- jsonp
- proxy

常用的是cors 只需要后端四行代码就可以搞定

jsonp的话 只是加它并不能处理跨域问题 因为它不能post请求

proxy是在项目开发的时候使用 上线了一般接口和项目都是在同一个服务器 也就不存在跨域问题了

### 说一下你知道的状态码

状态码主要分为5种类型
- 1xx 消息
- 2xx 成功
- 3xx 重定向
- 4xx 客户端错误
- 5xx 服务器错误

常见的状态码
- 200 成功
- 301 永久重定向
- 302 临时重定向
- 304 使用缓存不改变
- 401 请求授权失败
- 403 禁止访问
- 400 错误请求
- 404 找不到资源
- 500 服务器内部错误
- 504 网关超时

---
## 其他小分队🔫

### 常用的五个网站

1. GitHub
2. MDN中文网
3. 掘金
4. 相关技术官网文档
5. 哔哩哔哩

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
