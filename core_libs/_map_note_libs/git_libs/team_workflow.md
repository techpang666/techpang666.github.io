
# **团队工作流🤡**
>git不规范 程序员两行泪😭  
>独立的工作流场景命令👨‍💻  
* 开dev分支
* 开工作分支
* 推送工作分支
* 合并工作分支到dev分支
* 拉取dev分支回去工作分支
* 最后合并dev分支到master分支
* 处理冲突及退出vim编辑器
* 团队流中的一些坑

------
## **开dev分支**

```bash
# 一般项目都有master和dev分支(工作在dev分支或者基于dev分支开自己的工作分支)

# clone项目
git clone test.git
# 从远程的dev开个本地的dev分支(用于拉取合并远程的dev代码)
git checkout -b dev origin/dev
# 保险性拉取代码
git pull
```

------
## **开工作分支**
>**建议高密度push(方便救命)⭐**  

```bash
# 从dev那里开自己的工作分支(假设刚clone代码 默认在master分支)
git checkout -b techpang origin/dev
# 保险性拉取代码
git pull

# 是否推送工作分支看团队要求(建议推送为好 方便救命)
```

```bash
# 如果不小心从master中开了工作分支且写了代码(因为master的代码不一定及时 需要以dev分支为蓝本 开工作分支)

# 先push自己的代码(避免意外情况)
git push
git checkout dev
# 更新一下dev的代码
git pull
git checkout techpang
# 合并dev的代码
git merge dev
# push一下 清理工作台继续干活
git push

# 可能存在代码冲突 需要处理
```

------
## **推送工作分支**

```bash
# 常规git操作

# 不需要pull(因为工作分支是自己用 除非线上处理了什么东西就需要pull)
```

------
## **合并工作分支到dev分支**

```bash
# 先push自己的工作分支
git push
# 切换到dev分支
git checkout dev
# 一般都要拉取一下dev的代码(保险性操作)
git pull
# 合并工作分支的代码
git merge techpang
# 推送到dev分支
git push
```

------
## **拉取dev分支回去工作分支**

```bash
# 记得先推送自己的工作分支代码
git push
# 切换到dev分支
git checkout dev
# 更新一下dev的代码
git pull
# 切换回去工作分支
git checkout techpang
# 合并dev分支的代码
git merge dev
# push一下 清理自己的工作台 然后继续干活
git push
```

------
## **最后合并dev分支到master分支**

```bash
# 一般开仓人才有权限处理

# 合并所有工作分支的代码
git checkout techpang
git pull
git checkout dev
git pull
git merge techpang
git push

# 合并dev分支的代码到master
git checkout master
git pull
git merge dev
git push
```

------
## **处理冲突及退出vim编辑器**

```bash
# Automatic merge failed; fix conflicts and then commit the result.

# 出现这个的时候 根据提示找对应的文件解决冲突
# 一般代码冲突会出现在pull及merge的时候
# 解决冲突也是一种修改 需要commit
```

```bash
# 进入vim编辑器有两种情况 忘了先pull或者拉取(合并)同个文件

# 退出vim编辑器
:q
# 如果万一修改了需要退出(可以考虑直接用这个强推)
:q!
```

------
## **团队流中的一些坑**
>**习惯性status一下(防止踩坑)⭐**  

```bash
# 习惯性使用status检查当前分支的状态(防止踩坑)

# 记得去别的分支前先push自己的工作分支代码
# 去别的分支记得先pull
```

```bash
# failed to push some refs to

# 这种报错一般是忘了先pull就push造成的
# 或者分支有东西没有处理掉 status一下 根据提示处理掉即可
```

```bash
# 远程库覆盖本地库
git pull --rebase origin dev

# 如果万一不小心执行错了 重新拉一遍对应分支的代码即可

# 如果对应的分支没有push 可以用这个
git rebase --abort
# 放弃合并 回到操作rebase之前的状态 之前的提交不会被丢弃
```

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')