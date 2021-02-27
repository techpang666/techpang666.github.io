
# **响应代码**
>[相关资料](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status)  
* 信息响应(100-199)
* 成功响应(200-299)
* 重定向(300-399)
* 客户端错误(400-499)
* 服务器错误(500-599)

------
## **代码解读**
* `401`是没带token
* `404`是接口不存在

------
## **其他补充**

`token`的优先级比较高  
如果没有登录 不管访问什么接口 都会返回`401`  
请求数据的时候 发现接口错误就会返回`404`  

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')