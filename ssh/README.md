# ssh创建和使用

## 创建ssh
``` shell
ssh-keygen -t ed25519 -C "xiaoxm_001@outlook.com" -f ~/.ssh/github
```
注: -f是可选的，如果不写，默认放到~/.ssh/id_rsa

## 复制公钥到github
``` shell
cat ~/.ssh/github.pub
```

## 修改config文件
``` shell
Host github.com
User relax-admin
Port 22
IdentityFile /c/Users/Administrator/.ssh/github
```

## 从github下载私有仓库
``` shell
git clone git@github.com:relax-space/tmall-cookie-fetch.git
```
## 参考
https://docs.github.com/cn/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

## 问题

### 问题1: ssh: connect to host github.com port 22: Connection timed out

### 方案: 修改config文件
``` shell
Host github.com
Hostname ssh.github.com
User relax-admin
Port 443
IdentityFile /c/Users/Administrator/.ssh/github
```

### 问题2: ssh: connect to host ssh.github.com port 443: Connection refused
### 方案: 添加github证书到本地git
1. 找到git的ca文件, C:\Program Files (x86)\Git\mingw32\ssl\certs\ca-bundle.crt
2. 在浏览器搜索https://github.com,在搜索栏的左边点击小锁,下载github的cer证书, 用记事本打开,并复制到上面的文件中ca-bundle.crt,包括----BEGIN CERTIFICATE-------END CERTIFICATE---
### 引用

https://mattferderer.com/fix-git-self-signed-certificate-in-certificate-chain-on-windows

https://stackoverflow.com/questions/11621768/how-can-i-make-git-accept-a-self-signed-certificate