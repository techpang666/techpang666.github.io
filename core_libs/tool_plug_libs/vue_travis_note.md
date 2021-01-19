
# **通过Travis自动部署Vue项目**
>不要带参笔记 默认对象就好🌈  

------
## **操作流程大纲**
>相关教程[⚡](https://blog.csdn.net/qq_31126175/article/details/89353665)  
>配置翻车是家常便饭 一些操作自行搜索  
* 脚手架一个项目并GitHub托管(自动部署不支持码云⭐)
* 生成GitHub令牌
* 上Travis官网配置仓库
* Vue项目配置`.travis.yml`和`vue.config.js`
* 推送触发编译生成分支`gh-page`
* 仓库开启分支`GitHub page`功能
* 开始快乐起飞🚀

------
## **体验地址**
* [快乐起飞🚀](https://techpang.top/vue_page/)

------
## **相关配置文件**
* `vue.config.js`
* `.travis.yml`

```js
// vue.config.js

module.exports = {
  // vue_page是我的仓库名 这里改成你自己的仓库名
	publicPath: process.env.NODE_ENV === 'production' ? '/vue_page/' : '/',
};
```

```yml
# .travis.yml

# 基于Travis自动化部署vue项目起飞🚀

# 指定语言及版本
language: node_js
node_js: stable

# 安装项目包
install:
  - npm install

# 运行脚本
script:
  - npm run build

# 自动化编译推送GitHub
after_success:
  - cd ./dist
  - git init
  # 这是常规的git操作 可以自定义或者默认即可
  - git config --global user.name "travis"
  - git config --global user.email "666@gmail.com"
  - git add .
  - git commit -m "auto_push"
  # ${vue_page}改成自己配置的token名字 vue_page是我的token名字
  # @github.com后面的内容也是改成自己的 其实就是仓库地址去掉https部分
  - git push --quiet --force "https://${vue_page}@github.com/techpang666/vue_page.git" master:gh-page

# 触发自动化部署的分支
branches:
  only:
    - master
```

------
## **操作细节**
>记录一些细节操作  

token令牌在GitHub个人设置下的  
* `Developer settings`
* `Personal access tokens`
* `new token`
* 随便命名及勾选`repo`
* 记得保存下来(页面刷新就没了)

Travis官网配置token令牌  
* 在左边的`My Repositories`加号打开对应的仓库及设置
* 在`Environment Variables`中添加自己的token令牌
* 在`.travis.yml`配置文件中使用在官网添加的token令牌

开启仓库分支的`GitHub page`功能  
* 在自己的仓库首页选择`setting`
* 在下面有个`GitHub Pages`
* 在`None`选项中选择`gh-page`分支 `Save`一下
* 页面刷新后回到这个位置会看到有个可以访问的地址(部署需要时间 需要等一小会)

```bash
# 如果想提前开启分支的page功能 可以如下操作

git checkout -b gh-page
touch index.html
# 常规的git操作
git status
git add index.html
git commit -m "create_branch"
# 只需要操作一次 后面有需要的话直接push即可
git push --set-upstream origin gh-page
# 切换回主分支
git checkout master
# 这时候就可以提前去设置分支的page功能了(遇到Travis编译需要排队的时候 就可以这样玩 特别是晚上的时候)
```

------
## **🍊如意锦囊💰**
>收录各种注意点/疑难杂症(BUG/报错/疑问)及解决方案  

------
```js
console.log('code平平安安没有bug即如意');
```

------
commit信息不要带中文 编译不了(我就被坑了一个晚上加凌晨)⭐  

添加仓库的时候 看不到仓库就左边`Sync account`一下  

如果编译爆红就进行`Restart build`一下  

------
![end](https://gitee.com/techpang/img_emoji_libs/raw/master/img_bed/markdown_images/end.jpg '富婆加我吧不想努力了')