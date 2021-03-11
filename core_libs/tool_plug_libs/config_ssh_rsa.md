
# **配置免密登录服务器**

```bash
# 在服务器的根目录生成密钥(一路回车即可)
ssh-keygen
# 进入这个目录
cd /root/.ssh/
# 注入公钥到这个文件里面
cat id_rsa.pub >> authorized_keys

# 下载id_rsa密钥到用户名下的.ssh文件夹
```

## **总结一下**

流程应该是 在本地生成一对密钥

然后将公钥存在服务器的`/root/.ssh/authorized_keys`文件中
