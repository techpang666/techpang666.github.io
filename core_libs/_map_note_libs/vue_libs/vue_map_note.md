
## **VUE小分队佛系二级笔记**
>努力成为vue职业魔法师🔮  

```js
console.log('起飞起飞🚀');
```

------
学习路线  
* vue的基本用法
* vue的模板语法
* vue的常用特性
* 基于vue实现案例效果

vue.js 渐进式JavaScript框架 超快虚拟DOM 作者尤雨溪  
* 声明式渲染
* 组件系统
* 客户端路由
* 集中式状态管理
* 项目构建

vue基础 主要学习模板语法/视图渲染/组件/路由  
webpack和vue没有半毛钱关系 只是当前比较流行的前端构建工具  

vue不是一门语言 只是基于JavaScript封装的一套前端框架 有自己的API和开发模式 关键底层还是JavaScript的基础知识  
所以不要对框架的内容进行记忆 理解学会查阅官方文档  

传统的多页应用开发  
假设有一个带有三个页面的网站  
* 网站首页
* 产品列表
* 用户中心

每个页面有相同的结构  
* 顶部
* 底部
* 左边菜单
* 右边内容

现在有个需求 给每个页面的左边菜单加个广告  
实现方式 需要给三个页面修改添加广告  

单页应用开发就是 如何一个页面显示多个页面的内容  
内容一开始全部在一个页面中 通过JavaScript控制  
VUE开发的就是单页应用  

不需要跳转新的页面 重新加载页面 只需要在一个模板上 加载/卸载不同的子模版 显示内容  

按需食用 不用全部用上  

最核心的vue 实现模板引擎的声明式渲染  

MVVM是前端视图层的概念 关注视图层分离 MVVM将前端的视图层分为三部分  
* m(model数据层) vue中将数据层放在data中
* v(view视图) 即我们的html页面
* vm(view-model控制器) 将数据和视图层建立联系 vm就是vue的实例

下面的栗子中  
`html`就是视图模板  
`new Vue`就是vue的实例 数据变化 会更新到视图中 视图中的数据变化了 也会更新data中  
`data`就是model数据  

```html
<!-- 引入vue.js文件 -->
<script src="./libs/vue/vue.min.js"></script>

<!-- 添加模板结构 -->
<div id="app">
  <!-- 调用对象的属性 -->
  <div>{{msg}}</div>
  <div>{{arr}}</div>
</div>
```

```js
// 创建vue实例
new Vue ({
  // 指定模板
  el: '#app',
  data: {
    // 指定数据
    msg: '新手不要玩插件 多写基础语法',
    arr: [1, 2, 3]
  }
})
```

------
插件及工具推荐  
* vue devtools(chrome插件 不能用min.js 否则工具出不来 且需要开web服务(live server/npm run serve))
* Vetur(vscode插件 vue工具包)
* vueHelper(vscode插件 vue的code片段)

双向数据绑定体验  
只有表单元素才有效果 模板内容变化 数据跟着变化  

```html
<div id="app">
  <div>{{msg}}</div>
  <input type="text" v-model="msg">
</div>
```

```js
new Vue({
  el: '#app',
  data: {
    msg: '测试内容'
  }
})
```


------
脚手架配置初始化项目  

```bash
# 强烈建议使用git工具下包及切换淘宝源 乖听话🍌

# 找个干净的地方 新建项目文件夹 右击选择git工具 键入下面的命令
npm config set registry=https://registry.npm.taobao.org/

# 安装@vue/cli
npm install @vue/cli -g
# 安装webpack
npm install --save-dev webpack -g

# 如果使用的是webpack v4+版本 还需要安装CLI
npm install --save-dev webpack-cli -g

# 检查一下包是否下好了 如果装好了会输出版本号
vue -V
webpack -v

# 做好下包工作后 准备新建配置项目 如果是cmd/powershell 键入下面的命令
vue create my_vue

# 如果是git命令行工具 键入下面的命令(因为git默认不支持箭头及空格操作)
winpty vue.cmd create my_vue

# 自定义配置项目 方向键选择
manually select features

# 空格选择下面的 其他空格取消
Babel/css pre-processors
less
in dedicated config files

# 后面回车准备起飞🚀 项目初始化好了会出现下面两个命令 键入运行项目
cd my_vue
npm run serve

# 然后会弹出访问地址 两个都可以
http://localhost:8080/
http://127.0.0.1:8080/
```

------
vue项目目录理解  
```js
// main.js

import Vue from 'vue'
// 导入要渲染的单文件组件(.vue)
import App from './App.vue'

// 生产提示
Vue.config.productionTip = false

new Vue({
  // 渲染单文件组件
  render: h => h(App),
  // 挂载到页面元素中
}).$mount('#app')
```

```js
// App.vue

// 导入其他的单文件组件
import HelloWorld from './components/HelloWorld.vue'

// 对外暴露自己及导入的组件
export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
```

```vue
// 样式用的是`less`预处理器
// scoped 局部作用域样式 只对当前文件有效 解决样式冲突问题
<style lang="less" scoped>
</style>
```

------
第一个单文件组件落地  

```vue
// 单文件组件结构部分
<template>
  <div id="app">
    <!-- 只能一个根元素 vue3.0才支持多个 -->
    <h1>单文件组件开始起飞🚀</h1>
    <p>{{msg}}</p>
  </div>
</template>

// 单文件组件功能部分
<script>
// 用于暴露当前组件实例(template/script/style)
export default {
  // 暴露自己
  name: 'cv_center',
  // 暴露其他组件
  components: {
    test_components
  },
  // 返回数据
  data () {
    return {
      msg: '测试内容'
    }
  }
}
</script>

// 单文件组件样式部分
<style lang="less" scoped>
#app {
  color: pink;
}
</style>
```


------
vue的基本使用  

```html
<!-- 传统结构 -->

<div id="msg"></div>
```

```js
// 传统写法

let msg = '测试内容';
// * 原生写法
let div = document.getElementById('msg');
div.innerHTML = msg;
// * jq写法
$('#msg').html(msg);
```

```html
<!-- vue的结构 -->

<div id="app">
  <div>{{msg}}</div>
</div>
```

vue的基础语法  
* 插值表达式
* `v-model`
* `v-text`
* `v-html`
* `v-for`
* `v-if`
* `v-on`
* `v-bind`
* `v-show`

插值表达式解读  
```html
<!-- 将msg数据渲染到页面上 -->
<div>{{msg}}</div>
<!-- 插值表达式支持基本的计算操作 -->
<div>{{1 + 2}}</div>
<!-- 字符串拼接 -->
<div>{{msg + '----' + 123}}</div>
<!-- 如果是数字会进行计算操作 反之也是字符串拼接 -->
<div>{{msg + 123}}</div>
```

```js
// vue的基本使用

/**
 * @description vue的基本使用步骤
 * 
 * * 需求
 * 
 * * 构思
 * 提供标签用于填充数据
 * 引入vue.js文件
 * 使用vue做功能
 * 将vue的数据填充到标签中
 * 
 * * 总结
 * 
 */

// * 提供标签用于填充数据

// * 引入vue.js文件

// * 使用vue做功能
new Vue({
  // 挂载元素(值可以是选择器或者DOM元素)
  el: '#app',
  // 模型数据(值是个对象)
  // 存放要渲染到页面上的数据
  data: {
    // 会将HTML中的插值语法中的msg替换掉
    msg: 'hello vue'
  }
})

// * 将vue的数据填充到标签中
```

el 元素的挂载位置(值 选择器或者DOM元素)  
data 模型数据(值 一个对象)  

插值表达式 将数据插入到HTML标签中  
且支持基本的计算操作 `msg: 1 + 3`  

vue语法编译成原生语法  

前端渲染(数据绑定) 其实就是将数据填充到HTML标签中  

前端的渲染方式  
* 原生js拼接字符串
* 使用前端模板引擎
* vue特有的模板语法

原生js拼接字符串 将数据以字符串的方式拼接到HTML标签中  
缺点 每个开发者的风格不同 导致后期维护困难  

前端模板引擎有自己的模板语法规则 大家都按规则写code 便于后期维护  
缺点是没有专门的事件机制  



指令的本质就是自定义属性 格式`v-`开头 例如`v-cloak`  

`v-cloak`指令的用法  
插值表达式存在'闪动'问题 可以通过`v-cloak`指令解决  
原理是 先隐藏 替换好值后再显示最终的值  

```html
<style>
  /* 属性选择器 让有这个属性的标签先隐藏 */
  [v-cloak] {
    display: none;
  }
</style>

<div id="app">
  <!-- 添加自定义属性 -->
  <div v-cloak>
    {{msg}}
  </div>
</div>
```

通过属性选择器 选择带有`v-cloak`属性的标签 先隐藏  
给有插值语法的标签添加`v-cloak`属性  
当数据渲染完了 这个属性就会被去掉 属性选择器就找不到这个标签 自然对应的标签就变为可见了  

`v-text` 用于填充文本 和插值表达式类似 但没有闪动问题 比插值表达式更加简洁  
如果数据中有html标签 会一起输出(不会解析)  

`v-text`是单向绑定 数据对象的值改变 插值也会改变 但插值变化是影响不到数据对象的  

```html
<div id="app">
  <p v-text="msg"></p>
  <p>
    {{msg}}
  </p>
</div>
```

`v-text`指令中不要写插值写法 直接对应的变量名  
只有标签的内容才用插值表达式  

`v-html` 填充HTML片段 有安全问题 站点内部数据可以用 第三方数据不可以  

和`v-text`的区别是 前者会解析html标签 后者不会  

```html
<div id="app">
  <p v-html="html"></p> <!-- 标签会被解析 -->
  <p v-text="text"></p> <!-- 标签会源码输出 -->
</div>
```

```js
new Vue({
  el: '#app',
  data: {
    // * 这里不是反引号
    // * 习惯性加逗号 不然什么时候报错都不知道
    html: '<span>标签会被解析</span>',
    text: '<span>标签会被源码输出</span>',
  }
})
```

`v-pre` 填充原始信息 跳过某元素和其子元素的编译过程  
一些静态内容不需要编译 可以加这个指令加快渲染  

```html
<div id="app">
  <span v-pre>
    {{测试内容}} <!-- 直接输出'测试内容' -->
  </span>
  <br>
  <span v-pre>
    {{msg}} <!-- 即使data中定义了msg 还是会输出'msg' -->
  </span>
  <br>
  <span>
    {{msg}} <!-- 这里不加`v-pre` 就会输出data中的msg -->
  </span>
</div>
```

`v-once` 只编译一次 显示内容后不再有响应功能  
执行一次性的插值 当数据改变的时候 插值处不会再更新内容  

```html
<!-- 即使data中定义了msg 后期修改了msg值 还是显示第一次data中的msg值 -->
<span v-once>{{msg}}</span>
```

数据的响应式 数据的变化导致页面内容变化  
h5的响应式是根据屏幕尺寸的变化  

双向数据绑定 一处变化会导致另一处跟着变化  
* 当数据发生变化 视图也会跟着变化
* 当视图变化 数据也会同步更新
* 通过`v-model`实现

`v-model`限制在`<input>/<select>/<textarea>/components`中使用  

```html
<div id="app">
  <div>
    {{msg}}
  </div>
  <div>
    <input type="text">
    <!-- 输入框内容改变的时候 页面上的msg也会更新 -->
    <input type="text" v-model="msg">
  </div>
</div>
```

`v-on`用于绑定事件 `v-on:click`可以缩写为`@click`  

```html
<div id="app">
  <div>{{num}}</div>
  <div>
    <!-- 通过`v-on`给元素绑定事件 -->
    <button v-on:click='num++'>点击</button>
    <!-- 可以简写成`@click` -->
    <button @click='num++'>@click点击</button>
    <!-- `v-on`还可以接收需要调用的方法 -->
    <button @click='handle'>handle点击</button>
    <!-- 虽然加了() 但只有点击的时候才会被调用 -->
    <button @click='handle()'>handle()点击</button>
  </div>
</div>
```

```html
<button v-on:click='num++'>点击</button>
```
在html中使用data数据不需要`this` 是在定义函数中需要加`this`  
实际开发中 业务处理逻辑是很复杂的 所以不建议在`v-on`中写code 一般都是定义函数进行调用  

```html
<button v-on:click='handle'>点击</button>
<button v-on:click='handle()'>点击</button>
```
`handle`要和methods中的一致 `handle()`只有被点击的时候才会被调用  

```js
let vm = new Vue({
  el: '#app',
  data: {
    num: 0
  },
  // 在methods中定义函数
  methods: {
    handle: function () {
      // 这里的this就是vue的实例对象
      console.log(this === vm);
      // 在函数中 想要使用data中的数据 需要加this
      this.num++;
    }
  }
})
```

`methods`用于定义一些函数  
函数内部的`this`指的是vue的实例对象 且如果想要用data中的数据 需要加`this`  

```js
console.log(this === vm);
this.num++;
```



------
组件的体验  
单文件组件 一个拥有结构样式功能的整体  
组件主要用来描述某个页面或者其中的某个结构 用起来像标签  
为了组件能够在模板中使用 组件需要注册 注册类型分为全局和局部注册  
语法`Vue.component(组件名称, {配置})`  

创建组件需要在vue实例上面  

组件模板`template`只能一个根元素(顶级父容器) 不然会报错  
`Component template should contain exactly one root element`  

在vue中`template`用的是插值表达式`{{name}}` 不是`${name}`  

`data`必须返回一个对象 不然会报错  
`The "data" option should be a function that returns a per-instance value in component definitions`  
组件中的`data`必须是个函数 且要为每个实例返回一个值`return`  
因为组件是可以复用的 为了让组件都可以维护自己的数据 这就要求data必须是个对象且要`return`了  
对象本身是个地址 `{} != {}`  

在`template`中用了插值表达式`{{name}}` 别忘了`return`这个表达式 否则会报错  

`data () {}`是ES6的写法  
如果对象`Vue.component`内部的属性`data`是个函数 可以直接这样写 省略`: function`  

```js
Vue.component('test', {
  data () {
    return {
      msg: '测试内容'
    }
  }
})
```

```js
data: function () {
  return {
    name: '一号'
  }
},

// 上面ES5写法 这个是ES6写法
data () {
  return {
    name: '一号'
  }
},

// 这个会报错
// data: {
//   name: '一号'
// }
```

```html
<div id="app">
  <div>{{msg}}</div>
  <first></first>
</div>
```

```js
Vue.component('first', {
  template: `
  <p>我是组件</p>
  `
})

new Vue({
  el: '#app'
})
```

------
使用单文件组件(.vue)的用意  

`Vue.component`定义全局组件的时候 `new Vue({ el: '#app' })`需要给每个页面指定一个容器元素  

如果项目复杂或者项目由JavaScript所驱动的话 会有这些缺点  
* 全局定义(要求每个`component`不能重名)
* 字符串模板(缺乏语法高亮)
* 不支持CSS(template中很难写css)
* 没有构建步骤(浏览器不识别其他的语言 只认识html/css/js)





------
## **🍊如意锦囊💰**
>收录各种注意点/疑难杂症(BUG/报错/疑问)及解决方案  

------
```js
console.log('code平平安安没有bug即如意');
```






------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')