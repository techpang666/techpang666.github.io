
# **一些bug👹**

>Uncaught TypeError: Failed to execute 'appendChild' on 'Node': parameter 1 is not of type 'Node'

```js
document.head.appendChild('script')
document.head.appendChild(script)
```

>`<link rel=preload>` must have a valid `as` value

```html
<link rel="preload" href="./test.js">
<!-- This is a bug in Chrome, so we decided to leave it as is. -->
```



------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
