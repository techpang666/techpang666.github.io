
# **require和import的区别**
* 语法规范
* 加载方式
* 载入方式
* 导出类型
* 性能不同
* 导出值

## **语法规范**
* require是CommonJS规范的模块化语法
* import是ES6规范的模块化语法

## **加载方式**
* require是运行时加载
* import是编译时加载

## **载入方式**
* require可以写在代码的任意位置
* import只能写在文件的最顶端 且不可在条件语句或函数作用域中使用

## **性能不同**
* require运行时才引入模块的属性 所以性能相对较低
* import编译时引入模块的属性 所以性能稍高

## **导出类型**
* require是通过`module.exports`导出的值 不能再变化
* import是通过`export`导出的值 可以改变

## **导出值**
* require通过`module.exports`导出的是exports对象
* import通过`export`导出是指定输出的代码
