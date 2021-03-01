
## **Git小分队佛系二级笔记**
>万物之中 希望至美🌈  

------
### **内容大纲**
* git的介绍及安装
* git工具的优化
* git的开仓配置
* git的命令解读
* git的如意锦囊

------
### **git的简介**
* 工作区(status)
* 暂存区(add)
* 本地仓库(commit)
* 远程仓库(push)

------
### **git的安装**
>默认安装即可 懂就自定义安装  
>[国内镜像下载渠道](https://npm.taobao.org/mirrors/git-for-windows/)  

```bash
# 安装步骤详解

# vim 因为Linux就是vim编辑器
# use git from git bash only 最安全(如果要全局使用git就默认设置)
# use the openssl library 第二个有局限性
# checkout windows-style 行末换行符转换方式 默认即可
# use mintty 默认终端即可
# extra option 默认即可
# default behavior 默认即可
# git credential manager 默认就选这个
# enable file system caching 默认即可
# experimental support for pseudo consoles 默认不管
```

------
### **git工具的优化**
* 汉化git工具界面 右击选择`options/window/ui language` 选择`zh_CN`
* 取消滚动条 在上面的`window/scrollbar` 选择`none`
* 中文乱码 `text/locale`选择`zh_CN`
* 复制快捷键`ctrl + ins`
* 粘贴快捷键`shift + ins`
* 修改鼠标右键为复制粘贴 `mouse/click actions/right mouse button` 选择`paste` `middle`选择`nothing`

------
### **git的开仓配置**
* 线上开仓
* 配置提交者信息
* 提交时登录



线上开仓一般需要勾选  
* 仓库的自述文件 `README`
* 项目的忽略文件 `.gitignore`
* 项目的开源协议 `license`

开仓好后`clone`到本地就可以开始做项目了  

提交(commit)前需要配置一下提交者信息 随便配置 无论真假 和平台账号没有半毛钱关系  

但是如果想提交记录中有自己的头像信息 需要配置平台账号的邮箱  
名字还是可以随便 GitHub上看不到 码云可以看到  

```bash
# 配置提交者名字
git config --global user.name test_dev
# 配置提交者邮箱
git config --global user.email test@qq.com
```

提交者信息分项目级别和系统级别  
也就是加`--global`和不加的区别  

项目级别高于系统级别  
前者属于当前项目的  
后者属于当前系统的  

项目级别的提交者信息配置文件在项目中  
系统级别的在当前系统用户下  
可以`cat ~/.gitconfig`查看  

一般都是`--global`系统级别配置  
可以重新配置进行更新提交者信息  

推送(push)前需要登录一次平台账号(一般情况只需要登录一次即可)  

```js
console.log('乖听话 登录就对了🍌')
```

如果每次推送都需要密码 有两种方案  
* `git config --global credential.helper store`
* 配置密钥

第一种比较方便 跑一次命令后 再登录一次账号密码就可以了  
弊端就是 会生成文件进行明文密码  

第二种需要配置密钥 有点麻烦 但是安全  

```bash
# 通过git工具进入这个目录
cd ~/.ssh
# 生成对应的密钥文件
ssh-keygen -t rsa -C "平台账号的邮箱"
# 在用户名文件夹下面的.ssh中找到id_rsa.pub
# 复制内容到GitHub setting中
# 然后进行测试
ssh -T git@github.com
# 配置成功会如下输出
# You've successfully authenticated, but GitHub does not provide shell access.
```

------
### **git的命令解读**
>开仓测试命令  

```bash
# 检查本地仓库的状态(建议add前后检查一下仓库状态)
git status
# 检查仓库提交记录
git log
# 查看历史命令及版本号(后悔药)
git reflog
```

```bash
# 开工第一件事(拉取代码)
git pull
# 收工第一件事(推送代码)
git push
```

```bash
# 强制推送
git push -f
```

```bash
# git推送五步曲

# 检查仓库状态
git status
# 添加所有文件到暂存区
git add .
# 再次检查仓库状态
git status
# 提交本地仓
git commit -m "commit_msg"
# 推送远程仓
git push
```

```bash
# 添加全部文件到暂存区
git add .
# 将全部文件移出暂存区
git restore --staged .

# 可以是文件及文件夹
# 一般add操作是没有提示的 顶多会有一些warning提示 可以status检查一下仓库状态
```

```bash
# 提交本地仓
git commit -m "commit_msg"
# 撤销本地提交(撤销add及commit 不删除工作区代码)
git reset HEAD^

# HEAD^是上个版本的意思 也可以写成HEAD~1 两次则HEAD~2
```

```bash
# 恢复到上次commit的状态(高危操作 会删除工作区的code)
git reset --hard HEAD^
# 基于上个命令 如下操作 可以撤销远程提交记录(待测试)
git push origin HEAD --force
# 撤销已经push的操作(高危操作 上面的是还没push)
git revert HEAD^
```

```bash
# 撤销commit不撤销add(不删除工作区代码)
git reset --soft HEAD^

# 一般都是用git reset和git reset --hard
```

```bash
# commit直通车(直接add及commit)
git commit -m "commit_info" -a
```

```bash
# 修改最后一次提交的描述信息
git commit --amend -m "新的log信息"
```

```bash
# 打开当前文件夹
start .
# 通过编辑器打开当前文件夹
code .
```

```bash
# 初始化本地仓
git init
# 联动远程仓
git remote add origin 远程仓的地址.git
# 推送远程仓(可能会有main/master的差异)
git push -u origin master

# 以上操作一次即可 后期都是直接push
```

```bash
# 检查一下别名
git remote -v
# 给项目地址取个别名
git remote add name 远程仓的地址.git
```

```bash
# 分支操作系列

# 查看分支
git branch

# 创建分支
git branch branch_name

# 切换分支
git checkout branch_name

# 新建并切换分支(开发常用)
git checkout -b branch_name

# 修改当前分支的名称
git checkout -m new_branch_name

# 合并某分支的code到当前分支上
git merge branch_name

# 删除分支(需要在别的分支中操作)
git branch -d branch_name
```

```bash
# 如果已经add 再做修改的话会被删除
# 如果没有add 会恢复到上个版本号
# 一定要加-- 不然就变成切换分支了
git checkout -- .
```

```bash
# 查看全局配置
git config --global --list
# 查看当前仓库配置
git config --local --list
```

```bash
# 一行显示commit信息
git log --oneline
```

```bash
# 查看没有被追踪的文件
git ls-files --others
# 清理没有被追踪的文件
git clean -f
# 支持通配符 清理没有add的js文件
git checkout *.js
```

------
### **🍊如意锦囊💰**
>收录各种注意点/疑难杂症(BUG/报错/疑问)及解决方案  

------
```js
console.log('code平平安安没有bug即如意');
```

```bash
# 把git安装目录下的bin添加到系统变量path可实现全局git
# D:\Program Files\Git\bin
```

```bash
# gitee禁止公开邮箱导致的
failed to push some refs to
```

```bash
# 切换网路
git push 443
```

```bash
# 403错误的解决方案
git config --global credential.helper store
```

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')