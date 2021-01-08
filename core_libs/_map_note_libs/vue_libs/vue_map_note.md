
## **VUE小分队佛系二级笔记**
>努力成为vue职业魔法师🔮  

```js
console.log('起飞起飞🚀');
```

------
今日目标  
* vue的基本用法
* vue的模板语法
* vue的常用特性
* 基于vue实现案例效果

------
vue.js 渐进式JavaScript框架  
* 声明式渲染
* 组件系统
* 客户端路由
* 集中式状态管理
* 项目构建

超快虚拟DOM  
作者 尤雨溪  

------
vue的基本使用  

```html
<!-- 结构 -->

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

前端渲染 其实就是将数据填充到HTML标签中  

前端的渲染方式  
* 原生js拼接字符串
* 使用前端模板引擎
* vue特有的模板语法

原生js拼接字符串 将数据以字符串的方式拼接到HTML标签中  
缺点 每个开发者的风格不同 导致后期维护困难  

前端模板引擎有自己的模板语法规则 大家都按规则写code 便于后期维护  
缺点是没有专门的事件机制  

vue的模板语法  
* 插值表达式
* 指令
* 事件绑定
* 属性绑定
* 样式绑定
* 分支循环结构

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

------
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

------
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

------
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

------
`v-once` 只编译一次 显示内容后不再有响应功能  
执行一次性的插值 当数据改变的时候 插值处不会再更新内容  

```html
<!-- 即使data中定义了msg 后期修改了msg值 还是显示第一次data中的msg值 -->

<span v-once>{{msg}}</span>
```


















数据的响应式 数据的变化导致页面内容变化  
h5的响应式是根据屏幕尺寸的变化  



数据绑定 就是将数据填充到标签中  

双向数据绑定 一处变化会导致另一处跟着变化 通过`v-mode`实现  

```html
<input type="text" v-mode='uname'>
```

MVVM的设计思想  
* M(model)
* V(view)
* VM(View-Model)










































------
## **🍊如意锦囊💰**
>收录各种注意点/疑难杂症(BUG/报错/疑问)及解决方案  

------
```js
console.log('code平平安安没有bug即如意');
```






------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')