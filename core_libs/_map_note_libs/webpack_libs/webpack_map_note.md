
# **基于webpack打包项目**
>不要带参笔记 默认的事件对象就好🌈  

浏览器除了`html/css/js` 不识别其他code 这时候就需要构建工具打包code  

------
## **打包前准备工作**
>基于node的版本和webpack的版本冲突 需要先安装node@12.16.1  

```bash
# 先清理旧包
npm uninstall webpack -g
npm uninstall webpack-cli -g
```

```bash
# 安装指定版本的包
npm install webpack@4.44.1 -g
npm install webpack-cli@3.3.12 -g
# 检查包是否装好
webpack -v
webpack-cli -v
```

------
## **准备项目及代码**
```bash
# 初始化项目
npm init -y

touch index.html
mkdir src
cd src
touch app.js
touch getsum.js
```

```js
// getsum.js

function getSum(a, b) {
	return a + b;
}
module.exports = getSum;
```

```js
// app.js

import getSum from './getsum';
let sum = getSum(10, 20);
document.write(sum);
```

------
## **手动编译**
```bash
# 右击项目git bash
webpack ./src/app.js --mode=development

如果不加`--mode`会生成压缩版`main.js`
```

```html
<!-- 新建index.html 引入main.js -->
<script src="./dist/main.js"></script>
```

------
## **基于配置文件进行编译**
>编译命令`webpack`  

在项目根目录下创建配置文件 `webpack.config.js`  
* 入口(entry)
* 输出(output)
* 加载器(loader)
* 插件(plugin)

```js
// webpack.config.js

const path = require('path');
module.exports = {
	// 设置文件的入口：一开始就解析这个文件
	entry: './src/app.js',
	// 将入口文件解析为目标文件的配置
	output: {
		// 目标文件的输出路径文件夹名称
		path: path.join(__dirname, 'dist'),
		// 目标文件的文件名称
		filename: 'main.js',
	},
};
```

------
## **基于脚本配置进行编译**
>编译命令`npm run start`  

```json
// package.json

"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  // 自定义编译命令 这里是`start`
  // `--config`用于指定配置文件 实际工作中配置文件会很多
  // `--mode`如果不加的话会输出压缩版`main.js`
	"start": "webpack --config webpack.config.js --mode=development"
},
```

------
## **配置文件所需包**
>基于官网文档进行右击项目进行安装  
```bash
# 安装css-loader
npm install --save-dev css-loader
npm install --save-dev style-loader
# 安装less-loader
npm install less-loader --save-dev
# 安装file-loader
npm install file-loader --save-dev
# 安装babel-loader
npm install -D babel-loader @babel/core @babel/preset-env webpack
# 安装webpack-dev-server
npm install --save-dev webpack-dev-server
npm i webpack-dev-server@3.11.0 -g
# 安装html-webpack-plugin
npm install --save-dev html-webpack-plugin
# 安装vue-loader
npm install -D vue-loader vue-template-compiler
```

------
## **编译基本流程**
* 书写资源文件
* 引入资源文件
* 配置相关文件
* 重新编译
* 如果出错检查一下文件引入是否成功

------
## **处理css**
包包说明  
* `css-loader`是css解析器 可以将css解析为浏览器可以识别的类型
* `style-loader`可以自动的在指定文件中添加style标签 同时添加指定的样式代码

细节说明  
* 记得装包
* 记得导入
* 记得编译

```css
/* test.css */

/* 准备css资源 */
body {
  background-color: pink;
}
```

```js
// app.js

// 引入css
import '../style/test.css'
```

```js
// webpack.config.js

// 添加相关配置
const path = require('path');
module.exports = {
	// 设置文件的入口：一开始就解析这个文件
	entry: './src/app.js',
	// 将入口文件解析为目标文件的配置
	output: {
		// 目标文件的输出路径文件夹名称
		path: path.join(__dirname, 'dist'),
		// 目标文件的文件名称
		filename: 'main.js',
	},
	// 下面这个成员就是不同类型的文件的解析加载规则
	module: {
		rules: [
			// 配置的是用来解析.css文件的loader(style-loader和css-loader)
			{
				// 用正则匹配当前可被处理的文件的后缀名是  .css
				test: /\.css$/,
				// css-loader:读取css代码并解析为浏览器可以识别的代码
				// style-loader:把css代码添加到网页中
				use: ['style-loader', 'css-loader'], //webpack底层调用这些包的顺序是从右到左
			},
		],
	},
};
```

```bash
# 重新编译起飞🚀
npm run start
```

------
## **处理less**
实际开发中 我们会用`less/scss`这种预处理器进行创建样式  
但浏览器和webpack不能识别 需要包包辅助 处理流程和上面类似  
* 装包
* 配置
* 引入
* 编译

`less/css/style`三者的关系  
* less用于编译less为css代码
* css用于编译css代码
* style用于给浏览器添加css代码

```less
// test.less

// 变量结尾需要加冒号 不然会报错
// 不需要引号 会变成字符串
// 直接`@color`调用
@color: pink;
.box {
  border: 1px solid @color;
}
```

```js
// app.js

// 引入less
import '../style/test.less'
```

```js
// webpack.config.js

const path = require('path');
module.exports = {
	// 设置文件的入口：一开始就解析这个文件
	entry: './src/app.js',
	// 将入口文件解析为目标文件的配置
	output: {
		// 目标文件的输出路径文件夹名称
		path: path.join(__dirname, 'dist'),
		// 目标文件的文件名称
		filename: 'main.js',
	},
	// 下面这个成员就是不同类型的文件的解析加载规则
	module: {
		rules: [
			// 配置的是用来解析.css文件的loader(style-loader和css-loader)
			{
				// 用正则匹配当前可被处理的文件的后缀名是  .css
				test: /\.css$/,
				// css-loader:读取css代码并解析为浏览器可以识别的代码
				// style-loader:把css代码添加到网页中
				use: ['style-loader', 'css-loader'], //webpack底层调用这些包的顺序是从右到左
			},
			// 配置less解析
			{
				test: /\.less$/,
				use: [
					{
						loader: 'style-loader',
					},
					{
						loader: 'css-loader',
					},
					{
						loader: 'less-loader',
					},
				],
			},
			// 配置scss解析
			{
				test: /\.scss$/,
				use: [
					{
						loader: 'style-loader',
					},
					{
						loader: 'css-loader',
					},
					{
						loader: 'sass-loader',
					},
				],
			},
		],
	},
};
```

------
## 处理图片

## 利用Babel将ES6转换成ES5

## 监听项目变动自动刷新
不会生成dist文件夹  

## 自动导入资源文件生成HTML文件

## 让webpack解析vue单文件组件

## 完整的配置文件
>基于官网文档进行CV配置  
```js
// webpack.config.js

```

## 基于vue脚手架生成项目结构

------
## **🍊如意锦囊💰**
>收录各种注意点/疑难杂症(BUG/报错/疑问)及解决方案  

------
```js
console.log('code平平安安没有bug即如意');
```

------
无法加载文件`Roaming/npm/webpack.ps1`  
如果出现这种的错误 去相关路径删除`.ps1`文件  

------
如果编译过程提示需要安装`webpack-cli`  
```bash
# 这个包改装局部包
npm install webpack-cli@3.3.12
```

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')