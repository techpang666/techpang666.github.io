
# **eslint配置**
* 安装`eslint`
* 配置`eslint`
* 禁用保存格式化
* 项目配置对应的`.eslintrc.js`

```json
"eslint.run": "onType",
"eslint.options": {
    "extensions": [
        ".js",
        ".vue",
        ".jsx",
        ".tsx"
    ]
},
"editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
},
```

如果有其他的格式化插件  
在这个项目中 启动eslint 禁用另一个插件  

如果右下角的`eslint`爆红 就点击选择第一个`Allow Everywhere`  

测试发现 只要不打开保存时格式化就不用禁用其他插件  
避免冲突 还是建议关上吧 `eslint`配置已经保存时修复格式化了  

平时用`prettier` 项目需要再工作区开启`eslint`  


