
# **如何画0.5px的线**
* 采用metaviewport的方式
* 采用transform:scale()的方式
* 采用border-image的方式

------
## **采用metaviewport的方式**

```html
<meta name="viewport" content="width=device-width, initial-scale=0.5, minimum-scale=0.5, maximum-scale=0.5"/>
```

这样就能缩放到原来的0.5倍 如果是1px的话 就会变成0.5px

viewport只针对移动端有效果

`initial-scale=0.5`

------
## **采用transform:scale()的方式**

```css
transform: scale(0.5,0.5);
```

------
## **采用border-image的方式**
