
# **玩转服务器及Linux命令**
>莫要带参笔记 默认对象就好🌈  

------
## **玩转服务器**
* 可以通过`git/vscode`登录
* 给服务器安装`apt/git`

```bash
# 登录服务器的命令(vscode通过SSH插件配置登录)
# ssh –p端口号 用户名@IP地址
ssh –p22 root@127.0.0.1
```

```bash
# 安装apt工具
apt-get update -y
apt-get upgrade -y
# 安装git工具
apt install git
# 权限不够的时候可以加sudo
sudo apt install git
```

------
## **部署项目流程**
* 本地开发好服务器项目 测试能够正常访问就可以上云
* 一般项目存放在服务器的`/usr/local`
* 避免乌班图(Ubuntu)的包包版本不够 建议压缩包上传
* 打包部署项目及开放端口
* 想要关闭终端保持项目运行 需要开启守护进程(nohup node)

```bash
# 在项目的dist目录下
node app.js
# 开启守护进程
nohup node app.js
# 在防火墙中(或者安全组配置规则)开放对应的端口
TCP 3000
```

------
## **Linux目录详解**
```bash
# Linux系统根目录
cd /
# 用户的根目录
cd ~
# root用户的目录
cd /root
# 普通用户的根目录
cd /home/admin
# 项目存放路径
cd /usr/local
```

------
## **Linux命令详解**

------
```bash
# 删除文件
rm
# 删除空文件夹
rmdir
# 删除非空文件夹
rm -r
# 强制删除
rm -f
```

------
```bash
# 查找当前目录下的所有文件及文件夹
find .
# 查看当前目录下的文件及文件夹
ls
```

------
```bash
# 解压zip
unzip filename. zip
# 解压tar.gz
tar -zxvf filename.tar.gz
```

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')