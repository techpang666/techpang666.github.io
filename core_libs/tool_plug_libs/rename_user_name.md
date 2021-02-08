
# **如何修改系统用户名**

```bash
# 管理员运行CMD 开启Administrator账户
net user administrator /active:yes
```

然后注销选择`Administrator`登录 这时候就可以修改用户名文件夹了  

然后`Win+R`输入`regedit`打开注册表管理器  

在地址栏输入`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList`  
在子目录下的`ProfileImagePath`找到自己原来的用户名 改成和用户名文件夹一致即可  

这时候重启一下 注销登录原用户就可以了  

这时候可以去控制面板修改自己想要的或者一致的锁屏用户名了  

如果有环境变量 自己检查修复一下  

记得关闭超级管理用户`net user administrator /active:no` 建议重启一下  

最后 专业用户的电脑 不要这么搞 会一堆出错 想搞建议重装去搞  


