
# **Markdown佛系笔记**
>建议编辑器写 `ctrl+shift+p`键入预览 可以侧边预览  
>刚开始会觉得语法细节多不习惯 写多了就顺手了 markdown胜在书写干净舒服  
>语法都可以搭配使用及无限俄罗斯套娃 例如`>>**测试内容**`就是两层引用及字体加粗  
>支持HTML语法 例如想让图片居中等等就得用`img`标签  
>想加入表情符号 Win10可以<kbd>Win + ;</kbd>  
>推荐编辑器插件`markdown all in one` 可以优化书写体验 例如<kbd>ctrl + b</kbd>可以快捷加粗  
>更多玩法Google一下或者B站  

------
## **Markdown语法大纲**
* 标题
* 引用
* 段落
* 文本修饰(粗斜体/删除线/下划线)
* 分割线
* 无序及有序列表
* 代码块及代码段
* 链接
* 图片
* 其他语法(流程图/表格/键帽等等)

------
```md
<!-- 标题语法格式及举个栗子🌰 -->
井号+空格+标题

# 测试内容
### 三级标题
###### 最高六级
```

------
```md
<!-- 引用语法格式及举个栗子🌰 -->
右尖括号+内容+两个空格

>测试内容  
>不加空格 万一需要推送云端的时候 内容全跑一行去了  
>除了标题和列表 普通文字和引用都得两个空格  
>引用和下面的普通文字需要空行 不然就会被污染掉 即使普通文字不加引用语法  
```

------
```md
<!-- 段落语法格式及举个栗子🌰 -->
一个空行即段落

markdown没有缩进操作 tab键是代码段了  
```

------
```md
<!-- 文本修饰语法格式及举个栗子🌰 -->
一对星号即斜体
两对星号即粗体
三对星号即粗斜体
两对波浪线即删除线
一对`<u>`标签即下划线

*普通文字及引用记得追加两个空格换行 不然得哭真的*
**普通文字及引用记得追加两个空格换行 不然得哭真的**
***普通文字及引用记得追加两个空格换行 不然得哭真的***
~~普通文字及引用记得追加两个空格换行 不然得哭真的~~
<u>普通文字及引用记得追加两个空格换行 不然得哭真的</u>
```

------
```md
<!-- 分割线语法格式及举个栗子🌰 -->
三条中横线即分割线(我一般会图个好兆头 用六条)

------
```

------
```md
<!-- 列表语法格式及举个栗子🌰 -->
星号+空格+内容即无序
数字+点+空格+内容即有序

* 测试无序
1. 测试有序
  * 嵌套列表需要tab一下
```

------
```md
<!-- 代码语法格式及举个栗子🌰 -->
一对反引号即代码块
三对反引号即代码段(也可以tab键)

`let test = '代码块';`

<!-- ```js
可以指定代码语言 例如```js```
其他代码语言简写方式Google一下

console.log('代码段 这里会被污染影响下面的内容 所以我注释起来了');
``` -->
```

------
```md
<!-- 链接语法格式及举个栗子🌰 -->
中括号+小括号

[测试内容](test.com)
```

------
```md
<!-- 图片语法格式及举个栗子🌰 -->
感叹号+中括号+小括号

![编辑器只能引入 不能CV图片 可能需要依赖插件 我很少插图](test.jpg)
```

------
```md
<!-- 其他语法格式及举个栗子🌰 -->
流程图麻烦
表格麻烦
键帽还行 一对`<kbd>`标签即可
其他高级玩法Google一下

<kbd>Shift</kbd>
<kbd>Ctrl</kbd>
<kbd>Alt</kbd>
```



------
## **🍊如意锦囊💰**
>收录各种注意点/疑难杂症(BUG/报错/疑问)及解决方案  

------
```js
console.log('code平平安安没有bug即如意');
```

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')