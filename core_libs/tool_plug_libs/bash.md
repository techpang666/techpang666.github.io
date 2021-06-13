
# 一些常用的命令

## 配置开发环境系列

```bash
# 配置提交者名字
git config --global user.name test_dev
# 配置提交者邮箱
git config --global user.email test@qq.com
# 检查镜像源
npm config get registry
# 切换淘宝源
npm config set registry=https://registry.npm.taobao.org/
# 切换官方镜像源
npm config set registry=https://registry.npmjs.org/
# 安装vue脚手架
npm install @vue/cli -g
# 安装webpack
npm install --save-dev webpack -g
# 安装webpack脚手架
npm install --save-dev webpack-cli -g
# 安装ts编译工具
npm install -g typescript
```

## 一些创建项目的命令

```bash
# 创建vue项目
vue create super_vue
# 通过git创建vue项目
winpty vue.cmd create super_vue
# 创建react项目
npx create-react-app super_react
```

## 一些其他命令

```bash
# 检查当前的提交者名字
git config user.name
# 检查当前的提交者邮箱
git config user.email
# 查看文件内容
cat -n test.js
# 删除文件夹
rm -rf test_dir
# 恢复工作区变动
git checkout -- .
# 修改最后一次提交的信息
git commit --amend -m '新的log信息'
# 查看本地远程分支
git branch -a
# commit直通车(直接add及commit 新文件需要add一下)
git commit -m 'commit_info' -a
# 清理没有被追踪的文件
git clean -f
# 解决git反复需要登录账号密码的情况
git config --global credential.helper store
# 配置Mac的换行符
git config --global core.autocrlf true
```

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')
