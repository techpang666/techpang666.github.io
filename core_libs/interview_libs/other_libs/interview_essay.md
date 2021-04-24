
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

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
