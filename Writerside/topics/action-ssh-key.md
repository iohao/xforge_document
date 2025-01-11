# MAC 生成 SSH key

1.在本地生成ssh-key

执行下面命令，一路回车。

```
ssh-keygen -o -t ed25519
```

2.上传SSH Key到 git服务器

假设您的公钥存储路径为：~/.ssh/id_ed25519.pub

步骤：
1.登录gitee或github或其它，点击头像，然后选择「设置」或「settings」，找到SSH选项
2.`pbcopy < ~/.ssh/id_ed25519.pub`拷贝SSH Key。
3.添加到对应位置。

