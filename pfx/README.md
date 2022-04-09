# pfx
 有时候,要给自己打包的可执行文件做签名, 防止被杀毒软件查杀

## 如何开始

1. 安装signtool: 最后是在c盘搜索一下,如果有就直接用,没有的话,[下载](https://developer.microsoft.com/en-us/windows/downloads/windows-sdk/)
2. [生成pfx文件](../openssl/README.md)
3. 时间戳: 寻找可用的时间戳服务器: http://timestamp.comodoca.com/authenticode
4. 签名: 执行如下语句
``` bash
"C:\Program Files (x86)\Windows Kits\10\App Certification Kit\signtool.exe" /fd sha256 /f "C:\Program Files\OpenSSL-Win64\bin\cert\okjx.pfx" /p 1234  /t http://timestamp.comodoca.com/authenticode /v "C:\Program Files (x86)\okjx\okjx.exe"


# 输出
# The following certificate was selected:
#     Issued to: xiaomiao
#     Issued by: xiaomiao
#     Expires:   Tue Apr 06 11:14:26 2032
#     SHA1 hash: 96B3046C090352104C97D70D0FD27C81A5CE973A

# Done Adding Additional Store
# Successfully signed: C:\Program Files (x86)\okjx\okjx.exe

# Number of files successfully Signed: 1
# Number of warnings: 0
# Number of errors: 0
```

