
# **说一下圣杯布局和双飞翼布局的理解和区别并用代码实现**
- [圣杯布局demo](https://github.com/techpang666/html_css_js/blob/master/code/html/grail.html)
- [双飞翼布局demo](https://github.com/techpang666/html_css_js/blob/master/code/html/double_wings.html)

## **作用**
圣杯布局和双飞翼布局解决的问题是一样的

就是两边顶宽 中间自适应的三栏布局

中间栏要在 放在文档流前面 以优先渲染

## **区别**
- 圣杯布局

为了中间div内容不被遮挡

将中间div设置了左右`padding-left/padding-right`后

将左右两个div用相对布局`position: relative`并分别配合right和left属性

以便左右两栏div移动后不遮挡中间div

- 双飞翼布局

为了中间div内容不被遮挡

直接在中间div内部创建子div用于放置内容

在该子div里用`margin-left/margin-right`为左右两栏div留出位置

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
