
# 超级面试文档

## 导航大纲
- [html小分队](#html小分队)
  - [如何让a标签鼠标悬停变色](#如何让a标签鼠标悬停变色)
  - [元素的alt和title有什么异同](#元素的alt和title有什么异同)
- [css小分队](#css小分队)
  - [style标签写在body前和body后的区别是什么](#style标签写在body前和body后的区别是什么)
  - [简述下你理解的优雅降级和渐进增强](#简述下你理解的优雅降级和渐进增强)
  - [css可以继承的属性](#css可以继承的属性)
- [js小分队](#js小分队)
  - [Object是在堆还是栈里面](#Object是在堆还是栈里面)
  - [垃圾回收的两种方法](#垃圾回收的两种方法)
  - [说一下闭包](#说一下闭包)
- [一些其他的私有数据](https://github.com/techpang666/cloud_office/blob/master/markdown/interview_libs/setout/interview_essay.md)

## html小分队

### 如何让a标签鼠标悬停变色

```css
a:hover {
  color: pink;
}
```

### 元素的alt和title有什么异同

alt作为图片的**替代文字**出现，title作为图片的解释文字出现

## css小分队

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

## js小分队

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

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
