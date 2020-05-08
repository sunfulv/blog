# 在使用过代理后，调用python的requests库出现拒绝连接的异常

#### 问题

在windows10环境下，在使用代理(VPN)后。如果在python中调用requests库来地址访问时，有时会出现这样的错误，`ConnectionRefusedError:[WinError 10061] 由于目标计算机积极拒绝，无法连接`。如下图所示：

![image-20200508210458793](C:\Users\fulv\AppData\Roaming\Typora\typora-user-images\image-20200508210458793.png)

#### 解决办法

网上的大多数博客是通过修改默认浏览器中的代理设置来解决的，但是有时也会失效。根据博文

[windows注册表项配置客户端代理服务器](https://blog.csdn.net/hpp24/article/details/53375237)

通过删除注册表中的代理服务器设置，来解决这个问题。

首先找到代理服务器注册表项所在的位置

```
计算机\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings
```

然后删除掉ProxyServer项和对应的值。

![img](https://img-blog.csdn.net/20161128111600037?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

之后requests库就可以使用了。