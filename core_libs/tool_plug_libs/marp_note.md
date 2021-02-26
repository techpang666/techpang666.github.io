---
marp: true
---

## 这是一个由Marp输出的笔记
Marp for VS Code 程序员的PPT 🐂🍺  
Markdown All in One 增强编辑体验的插件  
>🎥<a href="https://www.bilibili.com/video/BV1Fy4y1k7vd/">演示视频</a>  
>📝<a href="https://sspai.com/post/55718">原教程地址</a>  

---
### 先锋队语法
    ---
    marp: true
    size: 4:3
    theme: default
    ---
通过上面的YAML语法代码告诉编辑器这是幻灯片不是文档  

---
### 基本操作
新建md及命令面板`Marp: Toggle Marp preview...`切换成幻灯片模式  
幻灯片的分页符`---` 第二页幻灯片需要在上面空行  
启动实时预览`Markdown: Open Preview` 快捷键`shift+ctrl+v`  
导出幻灯片`Export slide deck` 或者右上角图标选择  

---
### 特性及设置
* 支持Markdown原生语法  
* 各种Math公式渲染  
* 可以设置开启调用HTML元素 其实默认都行  
* 优化输出格式选择pptx及其他 默认pdf兼容性最好  

---
### 进阶玩法
可以在头部添加主题或者幻灯片比例等等属性  
或者在幻灯片内添加`<!-- $_类似HTML注释 -->`  
这种只会影响当前及后面的幻灯片  
想全局影响在前面加$  
只影响当前幻灯片加_  

---
### 样式命令
`theme: default` 主题  
`size: 4:3` 幻灯片比例  
`header/footer` 页眉页脚  
`paginate: true` 是否显示页码  
`color: pink` 字体颜色  
`backgroundImage` 背景图片  
`backgroundColor: pink` 背景颜色  
`# <!-- fit --> title` 用于标题自适应于幻灯片大小(最后幻灯片看效果)  
`headingDivider: true` 使用标题级别作分页标志  
保证输出markdown文档不会出现大量分割线(没听懂) 更多官方了解  

---
### 图片样式
`![bg w:200px cover vertical left:18% blur:15px](./test.jpg)`  
加bg就是背景图 反之图片 设置宽高  
可以填满幻灯片及纵向组合  
可以左右浮动留空间给内容  
可以模糊/亮度/对比度等滤镜操作  

---
### Markdown All in One插件
* 快捷键修饰内容
* 自动生成及更新目录
* 本地素材路径自动补全
* 自动格式化表格
* 数学公式加持

---
### Markdown All in One插件之快捷键
`Ctrl+b`加粗  
`Ctrl+i`斜体  
`Alt+s`删除线  
`Alt+c`是否勾选任务清单  
`Ctrl+m`启动Math公式  

---
### Markdown All in One插件之常用命令
`Markdown: Create Table of Contents`生成文档目录  
`Markdown: Update Table of Contents`更新文档目录  
`Markdown: Print current document to HTML`导出HTML文件  
`Markdown: Toggle code span`生成代码段  

---
<!-- _color: pink -->
### <!-- fit --> 有点东西
### <!-- fit --> 请把🐂🍺打在公屏上好嘛啦啦啦

---
### 感谢观看 **BY TECHPANG 201104**