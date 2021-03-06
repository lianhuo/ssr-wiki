# 方案一
在源码 server.py 所在目录下（自定义 config.json 可能不在这个目录），新建dns.conf文件，内容格式如下：
```
8.8.8.8 53
8.8.4.4 53
```
一行一个DNS服务器，端口可忽略，忽略时使用53端口，老版本的服务端不能支持此配置方式

#方案二
使用系统的DNS配置文件`/etc/resolv.conf`，添加内容：
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
不支持非53端口

服务端启动时会显示所使用的DNS，新版本优先使用方案一中的配置文件


# Custom DNS

Custom DNS is configured at the server side.

It allows the clients who requested remote DNS resolution on the server side to
query the domain names against whichever DNS server this file specifies.

## Configuration 1
At the source code folder (where `server.py` resides), put a new file
called `DNS.conf` with the following content:

```
8.8.8.8 53
8.8.4.4 53
```

1 DNS server per line, port number is optional. Server software versions less
than 2.9.4 do not support this feature.

## Configuration 2
Use the System default `resolv.conf`.

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Does not support non-53 ports by design.

If both are used, Configuration 1 will be eventually used.
