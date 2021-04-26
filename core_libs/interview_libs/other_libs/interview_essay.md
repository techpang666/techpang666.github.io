
# **一些面试题的快速记忆⚡️**
- 先看一遍再专项展开☕️

------

>async/await是什么

async/await es7新增的 是基于promise的

async用于声明一个异步函数

async会将常规函数转为promise 返回值也是一个promise对象

async函数内部可以使用await

await用于等待异步的功能执行完毕

放置在promise调用之前 会强制async函数中的代码等待 直到promise完成并返回结果

await只能和promise一起使用 只能在async函数内部使用

>相比较于promise async/await的优势

同步化代码的阅读体验 虽然promise摆脱了回调地狱 但是then链式调用的阅读负担还是有的

和同步代码更一致的错误处理方式 async/await可以用成熟的try/catch做处理 比promise的错误捕获更加简洁直观

调试的时候 阅读性会更友好

>什么是MVVM

model层 数据模型层 通过ajax/fetch等api完成客户端和服务端业务模型的同步

view层 视图层 作为视图模板的存在 view其实是个动态模板

viewmodel层 视图模型层 负责暴露数据给view层 并对view层中的数据绑定声明 指令声明 事件绑定声明 进行实际业务的实现

数据变化了 视图自动更新 viewmodel底层会监听object.defineproperty 当数据变化时 view层会自动更新

视图变化了 绑定的数据自动更新 会监听双向绑定的表单元素的变化 一旦变化 绑定的数据会自动更新

>MVVM的优缺点

优点

实现了视图和模型的分离 降低了代码的耦合 提高了视图或逻辑的复用性

提高代码的可测试性 viewmodel的存在可以帮助开发者更好的编写测试代码

能够自动更新DOM 利用双向绑定 数据更新后视图自动更新 让开发者从繁琐的手动操作DOM中解放出来

缺点

bug难以调试

因为使用了双向绑定 界面异常的时候 可能是view代码产生的bug

也有model代码的原因 数据绑定让一个位置的bug快速传递到其他位置 这样就导致想要定位原始出问题的地方就变得不容易了

解决方案

注释掉一段代码 确定代码的位置

debugger打断点或者console.log进行调试

在一个大的模块中model也会很大的 虽然使用方便 但是如果长期不释放内存 会造成更多的内存消耗 占用的是浏览器内存

>组件之间的通信方式

[props和$emit方式](https://github.com/techpang666/vue_relearn/blob/master/src/views/component_connection.vue)

eventbus事件总线

通过eventbus进行信息的订阅与发布(创建一个都能访问的事件总线)

```js
Vue.prototype.$eventBus = new Vue() /* this.$eventBus */

// a组件监听bus事件
this.$eventBus.$on('事件名', function(参数1, 参数2, ...) { ... })

// b组件触发bus事件
this.$eventBus.$emit('事件名', 参数1, 参数2, ...)
```














------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
