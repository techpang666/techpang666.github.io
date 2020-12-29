
## **NODE小分队佛系二级笔记**
>能一行笔记就不多解释(mark脑子里)  

```js
console.log('啦啦啦');
```

### NODE初体验

JavaScript需要借助node.js进行后端开发  

node.js是基于ChromeV8引擎的JavaScript运行环境 能对JavaScript进行解析  

node.sj运行环境包含两个部分  
V8引擎负责解析JavaScript code  
学习内置API进行后端开发  

node和浏览器的JavaScript运行环境区别  
浏览器是JavaScript的前端运行环境  
node是JavaScript的后端运行环境  

node的学习路线  
* JavaScript基础
* node.js内置API(fs/path/http)
* 第三方框架(express/mysql等等)

官方版本区别  
LTS 长期稳定版  
Current 新特性尝鲜版  

```bash
# 版本号 git/cmd查看
node -v
```

```js
// 终端node执行JavaScript code
node server.js
```

esc键 清空输入内容  
tab键 自动补全  
cls/clear 清空终端  


文件系统(fs)提供用来操作文件的模块  

```js
// 读取文件内容的方法
fs.readFile();
// 写入文件内容的方法
fs.writeFile();

// JavaScript需要导入fs模块
const fs = require("fs");

// 读取文件内容的语法
// 文件路径 编码格式(可选参数 以什么编码格式读取文件 默认utf-8) 回调函数
fs.readFile(path[, options], callback);

// 写入文件内容的语法
// 文件路径 写入内容 编码格式(可选参数 以什么编码格式写入文件 默认utf-8) 回调函数
// * 不会重复写入(追加内容) 覆盖旧内容
// * 只能创建文件 不能创建路径
fs.writeFile(file, data[, options], callback);
```

```js
// fs.readFile()的初体验

// 导入fs模块
const fs = require('fs');

// fs.readFile()的语法
fs.readFile('./node_note.md', 'utf8', function(err, data) {
  // 如果err为null 读取成功
  // 如果err为错误对象及data为undefined 读取失败
  console.log(err);
  // 打印数据
  console.log(data);
})
```

```js
// 通过判断err是否为null了解文件读取结果

const fs = require('fs');

// fs.readFile('./node_not.md', 'utf8', function(err, data) {
fs.readFile('./node_note.md', 'utf8', function(err, data) {
  if(err) {
    // ? 试错一下及为什么要return 可以不嘛
    // 错误信息 ENOENT: no such file or directory
    // return是拦截后面的code继续执行
    return console.log('文件读取失败：', err.message);
    // console.log('文件读取失败：', err.message);
  }
  console.log('文件读取成功，内容是', data);
})
```

```js
// fs.writeFile()的初体验

const fs = require('fs');

fs.writeFile('./test_write.md', 'test888', 'utf8', function(err) {
  // null证明写入成功 不会重复写入(追加内容) 覆盖旧内容
  // 只能创建文件 不能创建路径
  console.log(err);
  // * 这是写入 不是读取 所以读不到数据 undefined
  // console.log(data);
})
```

```js
// 通过判断err是否为null了解文件读取结果

const fs = require('fs');

// * 不存在的相关文件会自动创建
fs.writeFile('./test_write.md', 'test668', 'utf8', function(err) {
  if (err) {
    return console.log('写入失败', err.message);
  }
  console.log('写入成功');
})
```

```js
/**
 * @description 整理成绩
 * 
 * * 需求
 * 将成绩重新整理到新的文件中
 * 
 * * 构思
 * 导入fs模块
 * 使用fs.readFile()方法读取old成绩及判断一下是否读取成功
 * 
 * 处理成绩
 * 读取成绩按照空格进行分割(data.split())
 * 准备新数组及遍历替换操作(newArr.push(item.replace()))
 * 准备新字符串合并新数组(newArr.join("\r\n"))
 * 
 * 使用fs.writeFile()方法写入new成绩
 * 
 * * 总结
 * 数组的push()方法向数组尾部添加多个元素
 * '\r\n' 回车换行
 * 
 */

// * 导入fs模块
const fs = require('fs');
// * 使用fs.readFile()方法读取old成绩及判断一下是否读取成功
fs.readFile('./old.txt', 'utf8', function (err, data) {
  if (err) {
    return console.log('文件读取失败');
  }
  // * 获取成功 起飞
  // console.log(data);

  // * 处理成绩
  // * 读取成绩按照空格进行分割(data.split())
  const oldArr = data.split(' ');
  // * 准备新数组及遍历替换操作(newArr.push(item.replace()))
  // const newArr;  // * 粗心
  const newArr = [];
  oldArr.forEach((item) => {
    newArr.push(item.replace('=', ': '));
  });
  // * 准备新字符串合并新数组(newArr.join("\r\n"))
  const newStr = newArr.join('\r\n');
  // console.log(newStr);
  // * 使用fs.writeFile()方法写入new成绩
  fs.writeFile('./new.txt', newStr, 'utf8', function(err) {
    if (err) {
      return console.log('文件写入失败');
    }
    console.log('文件写入成功');
  })
});
```

fs路径问题  
./ 路径动态拼接 容易出错  
完整路径不利于后期维护  

```js
// 解决方案
// 通过`__dirname`解决路径拼接问题
// 表示当前文件所处目录

// fs.readFile(__dirname + './node_note.md', 'utf8', function(err, data) {
// * 这样拼接就只能这样写 '/node_note.md'
// Error: ENOENT: no such file or directory, open 'E:...\node_learn.\node_note.md'
fs.readFile(__dirname + '/node_note.md', 'utf8', function(err, data) {
})
```

路径模块(path)用于处理路径的模块  

```js
// 将多个路径片段进行拼接成完整的路径字符串
path.join()
// 从路径字符串中解析文件名
path.basename()

// 导入path模块
const path = rquire('path');

// path.join()的语法 [...paths] 路径片段序列
// 涉及到路径拼接 都要用path.join() 不要直接用+字符串拼接
path.join([...paths]);

// path.basename()的语法 path路径 ext文件扩展名(可选参数) 返回路径最后的一部分
path.basename(path[, ext]);

// path.extname()方法 获取文件的扩展名 
path.extname();
```

```js
// path.join()的练习

// 导入fs模块
const fs = require('fs');
// 导入path模块
const path = require('path');

fs.readFile(path.join(__dirname, '/test_node.md'), 'utf8', function (err, data) {
  if (err) {
    console.log(err.message);
  }
  console.log(data);
})
```

```js
// path.basename()的练习

// 导入path模块
const path = require('path');
// 模拟文件路径
const file_name = '/test/node/test_node.md'
// 获取文件名(带扩展名)
console.log(path.basename(file_name));
// 获取文件名(不带扩展名)
console.log(path.basename(file_name, '.md'));
// path.extname()方法 获取文件的扩展名 
console.log(path.extname(file_name));
```

http模块(用于创建web服务器)  
通过http.createServer()方法 本地创建web服务器 对外提供web资源服务  

```js
// 导入http模块
const http = require('http');
```

服务器和普通电脑的区别  
前者装了web服务器软件(IIS/Apache等等)  
后者通过nodejs的http模块就能手写服务器 对外提供web服务  

IP地址  
互联网每个电脑都是唯一的地址  
IP地址的格式 点分十进制(a.b.c.d) 都是0-255之间的十进制整数  
互联网的web服务器都有自己的IP地址  
例如 `ping www.baidu.com` 可以看到百度的服务器地址  
开发期间 自己即是服务器也是客户端 可以通过127.0.0.1进行访问  

域名(Domain Name)及域名服务器(DNS, Domain Name Server)  
域名和IP地址的关系都是对应的 存放在域名服务器中  
127.0.0.1对应域名localhost  

单纯使用IP地址都行 有域名可以访问更方便  

端口号  
一台电脑会运行很多个web服务 每个都对应一个端口号 不能被多个服务占用  
客户端通过端口号 可以准确的发送给对应的web服务  
80端口是默认的 可以忽略不写  
127.0.0.1:5500  

创建web服务器的步骤  
* 导入http模块(require('http'))
* 创建服务器示例(http.createServer())
* 给服务器绑定request事件(server.on('request'))
* 启动服务器(server.listen(5500))

req是请求对象 包含了客户端的相关数据和属性  
req.url 获取客户端请求的url地址  
req.method 获取客户端的请求类型  

res是响应对象 包含了服务器的相关数据和属性 例如将字符串发送给客户端  
向客户端发送的内容是字符串 需要加引号 不然服务器会挂掉  
res.end()方法 向客户端发送指定内容并结束这次请求  

防止中文乱码 需要设置响应头(res.setHeader())  

```js
// web服务器初体验

// 导入http模块
const http = require('http');

// 创建服务器实例
const server = http.createServer();

// 给服务器绑定request事件 监听客户端请求
server.on('request', (req, res) => {
  // 只要有客户端访问 就会触发request事件
  // console.log('访问服务器成功');

  // req是请求对象 包含了客户端的相关数据和属性
  // req.url 获取客户端请求的url地址
  // req.method 获取客户端的请求类型
  const str = `${req.url} -- ${req.method}`
  // console.log(str);

  // res是响应对象 包含了服务器的相关数据和属性 例如将字符串发送给客户端
  // res.end()方法 向客户端发送指定内容并结束这次请求
  // res.end(str)
  
  // 防止中文乱码 需要设置响应头
  res.setHeader('Content-Type', 'text/html; charset=utf-8')
  res.end('测试')
  
  // * 向客户端发送的内容是字符串 需要加引号 不然服务器会挂掉
  // res.end(666)
  // res.end('666')
})

// 启动服务器
server.listen(5500, () => {
  console.log('启动服务器成功');
})
```

```js
// web服务器练习

/**
 * @description 动态响应内容
 * 
 * * 需求
 * 根据不同的url响应不同的内容
 * 
 * * 构思
 * 创建web服务器
 * 
 * 获取url(req.url)
 * 设置默认响应内容(content=h4.404)
 * 
 * 通过if判断用户请求的是首页还是关于我们
 * url === '/' || url === '/index.html'
 * content.首页
 * url === '/about.html'
 * content.关于我们
 * 
 * 设置响应头防止中文乱码(res.setHeader())
 * 发送内容给客户端(res.end(content))
 * 
 * * 总结
 * 容易混淆req和res 前者是服务器请求客户端数据 后者是给客户端发送服务器数据
 * 现在是服务器请求客户端数据 所以是req 不是发送结果res给客户端
 * 
 */

// * 创建web服务器
const http = require('http');
const server = http.createServer();

server.on('request', (req, res) => {
  console.log('access success...');
  // * 获取url(req.url)
  let url = req.url;
  // * 设置默认响应内容(content=h4.404)
  let content = `
  <h4>404</h4>
  `
  // * 通过if判断用户请求的是首页还是关于我们
  if (url === '/' || url === '/index.html') {
    // * url === '/' || url === '/index.html'
    // * content.首页
    content = `
    <h4>首页</h4>
    `
  } else if (url === '/about.html') {
    // * url === '/about.html'
    // * content.关于我们
    content = `
    <h4>关于我们</h4>
    `
  }
  
  // * 设置响应头防止中文乱码(res.setHeader())
  // res.setHeader('Content-Type', 'text/html; chatset = utf-8');
  res.setHeader('Content-Type', 'text/html; charset=utf-8');
  // * 发送内容给客户端(res.end(content))
  // 打印一下当前的url
  // * 现在是服务器请求客户端数据 所以是req 不是发送结果res给客户端
  console.log(req.url);
  res.end(content);
})

server.listen(5500, () => {
  console.log('running...');
})
```

### 模块化

什么是模块化  
模块化是指解决一个复杂问题的时候  
自上而下的将系统划分成若干模块  
模块是可以组合/分解/更换的单元  

编程领域的模块化  
就是遵守规则  
将大文件拆成独立并相互依赖的多个小模块  

模块化的好处  
* code的复用性
* code的可维护性
* 可以按需加载

模块化需要遵守规则  
* 使用什么语法引用模块
* 什么语法向外暴露成员

模块化规范的好处是大家遵守模块化的规范写code 降低沟通成本 方便各个模块的相互调用  

node的三大模块化分类
* 内置模块(fs/path/http等等)
* 自定义模块(用户自己的)
* 第三方模块(第三方开发的 非官方模块 需要提前下载)

```js
// 内置模块
const http = require('http');

// 自定义模块 使用require()方法加载时 可以省略.js后缀名
const custom = require('./custom.js')
// 加载模块会执行模块中的code
console.log('我是自定义模块');

// 第三方模块
const moment = require('moment')
```

模块的作用域  
模块的作用域和函数的作用域一样 自定义模块中的变量/方法等成员 只能内部访问 外部访问不了  
防止全局变量的污染/文件依赖等问题的产生  

module对象  
每个自定义模块中都有一个module对象 其中module.exports对象可以将模块内的成员共享给外界使用  
require()方法导入的自定义模块 得到的就是module.exports所指的对象(其他属性及方法都作废)  

module.exports会把属性值都JSON连起来 不管是单双引号 都格式化掉  

```js
console.log(module);
```

```js
// 加载自定义模块.js

const mo = require('./test_module')
// 打印结果 { username: '小黑', sayHi: [Function: sayHi] }
console.log(mo);
```

```js
// 自定义模块.js

console.log('我是自定义module');

// 向module.exports对象挂载username属性
module.exports.username = '张三';

// 向module.exports对象挂载sayHello()方法
module.exports.sayHello = function () {
  console.log('我是sayHello()方法');
}

// 使用module.exports指向新的对象
// * 通过require()方法导入模块的时候 导入结果以module.exports指向的对象为准
// * 通俗点讲就是 前面的属性及方法都废了 以对象为准
module.exports = {
  username: '小黑',
  sayHi() {
    console.log('Hi小黑');
  }
}

// 基于模块的作用域 这些变量及方法是访问不到的 返回的是空对象{}
// const username = '张三';
// function sayHello() {
//   console.log('说话');
// }
```

exports对象  
因为module.exports对象单词太长 简化对外共享成员的code nodejs提供了exports对象  
一般两者都是指向一个对象 但最终结果以module.exports指向的对象为准  
防止混淆 不要在模块中同时使用两者  

```js
// 两个对象的比较

console.log(module.exports);
console.log(exports);
// 默认情况 两者都是指向同一对象
console.log(module.exports === exports); /* 打印结果为true */
```

```js
// exports对象的体验

// 将成员进行共享
exports.username = '张三';
// 直接挂载方法
exports.sayHello = function () {
  console.log('这是sayHello()方法');
}
```



```js
// 两个对象的打印测试

exports.username = '张三'; /* 不会打印 */
module.exports = {
  gender: '男',
  age: 22
}
```

```js
// 两个对象的打印测试

module.exports.username = '张三';
// 不会执行
exports = {
  gender: '男',
  age: 22
}
```

```js
// 两个对象的打印测试

// 都会执行 因为内部没有指向新的对象 内部即module.exports对象
module.exports.username = '张三';
// * 都会把属性值JSON连起来 不管是单双引号 都格式化掉了
// exports.gender = "男";
exports.gender = '男';
```

```js
// 两个对象的打印测试

// 三个都会打印 因为这个exports赋值给module.exports
exports = {
  gender: '男',
  age: 22
}

module.exports = exports;
module.exports.username = '张三';
```


nodejs遵循CommonJS模块化规范 CommonJS规定模块的特性及各个模块之间的相互依赖  
* 每个模块内部 module变量代表当前模块
* module变量是一个对象 其中的exports属性(module.exports)就是对外接口
* require()方法加载模块 就是加载该模块的module.exports属性

包包包  
nodejs中第三方模块也叫包  
不同于内置及自定义模块 包来自第三方团队开发的 nodejs的包都是开源的  

为什么需要包  
因为内置模块只是提供一些底层API 导致基于内置模块进行开发的时候 效率低  
包是基于内置模块封装的 提供更加高级方便的API 提高开发效率  
包和内置模块的关系 类似jQuery和浏览器内置API  

如何下包  
一般都是从npm(Node Package Manager 包管理工具)下载 nodejs已经内置npm  

```bash
# 终端检查npm版本
npm -v

# 检查镜像源(下包前/切换了也要检查一下)
npm config get registry
# 打印结果 https://registry.npmjs.org/

# 切换国内淘宝镜像(因为npm服务器在境外 下包慢)
npm config set registry=https://registry.npm.taobao.org/

# 上传包需要切换官方镜像地址
npm config set registry=https://registry.npmjs.org/
```

```bash
# nrm小工具(辅助切换镜像等等)的安装及使用(不影响npm原生的使用)
# 教程链接 https://segmentfault.com/a/1190000017419993
# 体验下来发现 装不装都无所谓 图方便就装一下(nrm use 用来切换源还是挺香的)

# nrm的安装
npm i nrm -g
# 下载成功的打印结果 added 494 packages from 893 contributors in 39.058s

# 检查版本
nrm --version
# 查看可选择源 星号表示正在使用的源
nrm ls
# 测试源的速度
nrm test
# 切换源
nrm use npm
# 添加源 源名 源地址
nrm add taobao https://registry.npm.taobao.org/
# 删除源(不能删内置的) 源名
nrm del taobao
```

```js
// 格式化时间

// 导入自定义模块
const time = require('./format_date')

// 获取系统时间
const dt = new Date();
console.log(dt);

// 格式化时间
const newDT = time.dateFormat(dt);
console.log(newDT);
```

```js
// 格式化时间的自定义模块

// 封装格式化时间函数
function dateFormat(dtStr) {
  const dt = new Date(dtStr);

  const y = dt.getFullYear()
  const m = padZero(dt.getMonth() + 1)
  const d = padZero(dt.getDate())
  
  const hh = padZero(dt.getHours())
  const mm = padZero(dt.getMinutes())
  const ss = padZero(dt.getSeconds())
  
  return `${y}-${m}-${d} ${hh}:${mm}:${ss}`
}


// 封装补零函数
function padZero(n) {
  // 返回三元表达式 如果n大于9 输出n 反之加零
  return n > 9 ? n : '0' + n;
}

// 对外共享方法
module.exports = {
  dateFormat
  // ? 测试带括号情况 直接调用方法
  // * 直接报错完蛋
  // dateFormat()
}
```

```js
// 使用第三方包格式化时间

// 终端使用nmp安装项目所需包(moment)
// npm i moment

// 导包
const moment = require('moment')
// 参考文档 调用moment()方法 获取当前时间 再通过format()方法格式化时间 一套连招带走
// const dt = moment.format('YYYY-MM-DD HH:mm:ss')
const dt = moment().format('YYYY-MM-DD HH:mm:ss')
console.log(dt);
```

```bash
# 如果想指定版本的包 需要加个@ 同时可以多包安装
npm i moment moment@2.22.2
```

下包产生的node_modules和pageage-lock.json的作用  
* node_modules存放的是下载的第三方包 require()方法导包就是从这里查找的
* pageage-lock.json用来记录下包的版本等信息

npm规定 每个包的根目录 必须有个package.json记录它的配置信息  
* 项目名称/版本号/描述等
* 项目都用到哪些包
* 哪些包是开发阶段使用的
* 哪些包是开发和部署都要用的

理解package.json配置文件的作用  
第三方包的体积过大 不利于团队共享  
解决方案是 共享时剔除node_modules文件夹  

package.json和package-lock的区别  
* 前者init产生的(记录着项目安装的包)
* 后者是下包产生的(记录着包的版本/地址)

如何记录项目中安装了哪些包  
在项目的根目录创建package.json配置文件 记录安装了哪些包 方便剔除  

实际开发通过.gitignore添加node_modules文件夹  

```bash
# 快速创建package.json配置文件(一路回车)
# 只能英文路径及命名 不能中文及空格
npm init
```

安装包的时候 npm会将包的信息记录在package.json的dependencies节点里面  
当我们拿到没有node_modules的项目 可以`npm i`安装所有的包

```bash
# 卸载指定包
npm uninstall moment
```

devDependencies节点的作用(一般都不用管 如果给别人用的话)  
如果有包只是开发阶段使用 那就保存在这个节点 反之dependencies节点  

```bash
# 下包到devDependencies节点
npm i moment --save-dev
# 简写模式
npn i moment -D
```

包的分类  
* 项目包(在项目的mode_modules中的都是)
* 全局包(在用户目录下的Roaming\npm\node_modules)

项目包又分两类  
* 开发依赖包(在devDependencies节点的包 只会开发阶段用)
* 核心依赖包(在dependencies节点的包 开发部署都要用的包)

```bash
# 核心依赖包
npm i moment
# 开发依赖包
npm i moment -D
```

全局包  
一般都是工具性质的包才有必要 提供便捷的终端命令  

```bash
# 安装全局包
npm i nrm -g
# 卸载全局包
npm uninstall nrm -g
```

```bash
# i5ting_toc可以将markdown转为html
i5ting_toc -f ./test.md -o
```

开发包的流程  
* 规范的包结构


规范的包结构需要三点要求  
* 包以独立目录存在
* 包的根目录要有package.json配置文件
* package.json要有三个属性(name/version/main) 代表包的名字/版本/包入口
* 更多规范 参考这个网址[🌏](https://classic.yarnpkg.com/zh-Hans/docs/package-json)

初始化包的基本结构  
* 新建包根目录
* 新建三个文件(package.json/index.js/README.md) 包管理配置文件/包的入口文件/包的说明文档

package.json的main作用  
在导入的时候 如果没有指定的特定文件 却能获得包的返回内容  
这是因为node的require()方法 如果没有发现具体文件 会找package.json其中的main属性  
如果有 则执行main属性对应的文件  

```js
// 测试代码
// * 不对外共享就会报错

// 导入自定义模块
const itheima = require('./index')

// 转义 Html 字符串
const htmlStr = '<h4 title="abc">这是h4标签<span>123&nbsp;</span></h4>';
const str = itheima.htmlEscape(htmlStr);
console.log(str);

// 还原 Html 字符串
const resetHtml = itheima.htmlUnEscape(str);
console.log(resetHtml);
```

```js
// 定义转义及还原HTML的方法

// 定义转义 HTML 字符的函数
function htmlEscape(htmlstr) {
  return htmlstr.replace(/<|>|"|&/g, (match) => {
    switch (match) {
      case "<":
        return "&glt;";
      case ">":
        return "&gt;";
      case '"':
        return "&quot;";
      case "&":
        return "&amp;";
    }
  });
}

// 定义还原 HTML 字符的函数
function htmlUnEscape(str) {
  return str.replace(/&glt;|&gt;|&quot;|&amp;/g, (match) => {
    switch (match) {
      case "&glt;":
        return "<";
      case "&gt;":
        return ">";
      case "&quot;":
        return '"';
      case "&amp;":
        return "&";
    }
  });
}

// * 不对外共享就会报错
module.exports = {
  htmlEscape,
  htmlUnEscape,
};
```

包的说明文档建议规范(包的作用/用法/注意事项等等)  
* 安装方式(`npm i`)
* 导入方式(require()方法)
* 格式化时间(`.dateFormat()`)
* 转义HTML中的特殊字符
* 还原HTML中的特殊字符
* 开源协议(ISC)

注册账号上传包建议翻墙操作  
[全局翻墙蓝灯选手](https://github.com/getlantern/lantern)

```bash
# 在项目的根目录中打开终端/git bash

# 登录npm账号
npm login

# 发布包(需要切换回npm官方服务器)
npm publish
# 发布成功应该没有报错信息

# 删除包
npm unpublish package_name --force
# 只能删除72小时内的包 然后24小时内不能再发了
# 不要乱发没有意义的包
```

模块的加载机制  
优先从缓存中加载 提高模块的加载效率  
模块第一次加载后会被缓存 不会因为多次调用require()方法导致模块的code多次执行  

```js
// 调用自定义模块 test_code.js

const custom = require('./custom')
const custom = require('./custom')
const custom = require('./custom')
```

```js
// 自定义模块 custom.js

console.log('啦啦啦');
```

内置模块的加载优先级最高 即使node_modules目录下有个同名包  

```js
const fs = require("fs"); /* 返回的是内置fs模块 */
```

自定义模块的加载机制  
使用require()方法加载自定义模块的时候 必须以`./`开头  
不然会被当是内置或者第三方模块  

自定义模块如果没有扩展名 node会执行下面的顺序进行加载  
* 补全.js进行加载
* 补全.json进行加载
* 补全.node进行加载
* 加载失败 终端报错

所以要规范加扩展名  

第三方模块的加载机制  
如果不是内置也不是自定义模块 node会从当前模块的父目录开始 在node_modules目录加载第三方模块  
如果没有找到对应的第三方模块 会移动到再上层父目录 进行加载 直到文件系统的根目录  

```bash
# 全网找tools第三方模块

C:\Users\itheima\project\foo.js
# 假设在foo.js文件中调用tools第三方模块 node会进行这样的查找

# project项目下的node_modules
C:\Users\itheima\project\node_modules\tools
# 项目外的node_modules
C:\Users\itheima\node_modules\tools
# 用户下的node_modules
C:\Users\node_modules\tools
# 文件系统根目录下的node_modules
C:\node_modules\tools
```

当把目录作为模块标识符 会有三种加载方式  
* 在被加载的目录下找package.json文件 其中的main属性作为require()加载的入口
* 如果没有json文件或者main解析失败 会尝试加载index.js文件
* 都没有就会终端报错 `Error: Cannot find module xxx`

### express框架

类似内置的http模块 用于创建web服务器的  
本质 第三方包 提供快速创建web服务器  

不用express也能创建web服务器(内置http模块)  
内置模块开发效率低 express是基于http模块进一步封装的 提高开发效率  
两者之间的关系 类似webAPI和jQuery的关系  

常见的服务器有两种  
* web网站服务器 用于提供web网页资源的服务器
* API接口服务器 用于提供API接口的服务器

express就可以做这两种服务器  

```js
// express初体验

// 导入第三方模块
const express = require('express')

// 创建服务器
const app = express();

// 监听get/post请求 返回数据
// url 客户端请求的地址
// req 请求对象(包含请求的属性与方法)
// res 响应对象(包含响应的属性与方法)
app.get('/', function (req, res) {
  // console.log(req, res);

  // 通过req.query对象 获取url中携带的查询参数
  // 客户端请求的 ?name=zs&age=20 可以通过req.query对象查到 默认空对象
  // req.query.name req.query.age
  console.log(req.query);
  res.send(req.query)
  // 通过res.send()方法 将处理好的内容 发送给客户端
  // 向客户端发送JSON对象
  // res.send({name: '张三', age: 20, gender: '男'})
})

app.post('/', function (req, res) {
  // console.log(req, res);

  // 如果客户端给你个post 你返回给字符串(请求成功)
  res.send('请求成功')
})

// 调用app.listen(端口号, 回调函数)启动服务器
app.listen(5500, function () {
  console.log('running...');
})
```

转换一下思维 或者说角色 你现在处于后台 不是客户端向服务器GET/POST  

监听客户端的GET/POST请求  
```js
app.get()
app.post()
```

通过req.query对象 获取url中携带的查询参数  
```js
// test.com?name=zs&age=20

// * res/req 别参数混淆了
res.send(req.query.name)
```

通过req.params对象获取url中动态参数  
* 默认空对象
* `/:id` id命名可以改的 可以多个参数 `/:id/:name`
* 展示到页面的id键 是自定义的变量值

```js
// url参数中 可以通过:参数名 匹配动态参数值
app.get('/user/:id/:name', (req, res) => {
  // req.params存放着通过:动态匹配的参数值 默认空对象
  console.log(req.params);
  // 一定要给客户端发送东西才不会转圈
  res.send(req.params);
})
```

log和send的区别  
* log是给服务器打印的 不是客户端控制台的
* send是给客户端发送内容的 一定要给客户端发送东西才不会转圈
```js
console.log('666');
res.send('666');
```

现在，你就可以访问 public 目录中的所有文件了： 
访问图片资源： 
访问 css 资源： 
访问 js 资源：

http://127.0.0.1:5500/


调用express.static()方法 对外提供静态资源  
```js
app.use(express.static('public'))

// 就可以访问public目录中的所有文件了
// 存放静态文件的目录名不会出现在url中

// http://127.0.0.1:5500/images/test.jpg
// http://127.0.0.1:5500/css/style.css
// http://127.0.0.1:5500/js/test.js
```

可以多次调用expres.static()方法 托管多个静态资源  
```js
app.use(express.static('public'))
app.use(express.static('file'))
```

如果想挂载路径前缀 可以这样操作  
记得加`/`  
```js
app.use('/public',express.static('static'))

// 存放静态文件的目录名不会出现在url中
// 所以下面会显示public前缀 不会显示static

// http://127.0.0.1:5500/public/images/test.jpg
// http://127.0.0.1:5500/public/css/style.css
// http://127.0.0.1:5500/public/js/test.js
```

nodemon工具可以监听项目的变动 自动重启项目  
```bash
# 全局安装nodemon
npm i nodemon -g

# 常规启动服务器
node server.js

# 改用nodemon运行项目
nodemon server.js
```

```js
// 导包
const express = require('express')

// 创建服务器实例
const app = express();

app.get('/', function (req, res) {
  console.log('服务器 我来了 666');
  res.send('客户端 我知道了 666')
})

// 启动服务器
app.listen(5500, function (req, res) {
  console.log('running...');
})
```











------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')