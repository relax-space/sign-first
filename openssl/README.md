# openssl
    通过openssl生产pfx文件

## 如何开始

1. 安装openssl

https://slproweb.com/products/Win32OpenSSL.html

最关键的是,找到一个可以用的openssl.conf

2. 生成pfx
``` bash
# 第一步: 生成key
openssl genrsa -des3 -out app.key 2048
# 第二步: 生成crt
openssl req -new -x509 -key app.key -out app.crt -days 3650
# 第三步: 生成pfx
openssl pkcs12 -export -out app.pfx -inkey app.key -in app.crt

```
3. 验证是否生成成功

方法一:
    1. 双击app.pfx, 然后一直下一步直到完成
    2. 打开ie 或edge, 在设置->隐私 搜索和服务 找到 管理证书
方法二:
    1. 在cmd或者powershell中执行 `certutil -dump "C:\Program Files\OpenSSL-Win64\bin\cert\okjx.pfx"`

## 引用

https://blog.csdn.net/WeLoveSunFlower/article/details/84951818
