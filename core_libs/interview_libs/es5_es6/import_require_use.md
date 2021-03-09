
# **require和import的使用**
* require
* import

## **require**
* **定义模块**

module变量代表当前模块 它的exports属性是对外的接口

通过exports可以将模块从模块中导出 其他文件加载该模块实际上就是读取`module.exports`变量 这里可以是变量/函数/对象等

在node中 如果用exports进行导出的话 系统会帮您转成`module.exports`的 只是导出需要定义导出名

```js
// 常规导出
module.exports = {...}
// 在node中可以通过exports导出 需要定义方法名
exports.data = {...}
```

* **加载模块**

`require`方法用于加载后缀为js的模块文件

```js
// 导入node的文件系统模块
const fs = require('fs')
// 导入自定义模块
const test = require('./test')
```

## **import**
* **定义模块**

在模块中可以使用`export`关键字可以将变量/对象/函数/类等从模块中导出 再通过`import`语句就可以使用它们

一个模块中只能有一个默认导出`export default` 但可以有多个export导出

```js
// 导出默认对象
export default{...}
// 导出自定义方法
export function test() {...}
```

* **加载模块**

import加载模块可以有多种形式

可以整个模块的内容/单个接口/多个接口/别名接口/默认值等方式载入
可以实现按需加载模块 提高代码的性能

```js
// 导入整个对象(和export default配套)
import test from 'test'
// 解构导入
import { test, post } from 'test'
// 通过别名导入
import { test as name } from 'test'
```
