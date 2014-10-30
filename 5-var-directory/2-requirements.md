## 要求

`/var`下要求有这样的文件夹或符号链接。

文件夹	|描述
--------|--------------------------
cache	|应用程序缓存数据
lib	|可变状态信息
local	|`/usr/local`的可变数据
lock	|锁文件
log	|日志文件和文件夹
opt	|`/opt`的可变数据
run	|有关正在运行进程的数据
spool	|应用程序spool数据
tmp	|系统两次启动之间保留的临时文件

有几个文件夹是‘**保留的**’，就是说，轻易不许一些新的应用程序使用它们，有可能与旧的或系统中的用法冲突。它们是：

* /var/backups
* /var/cron
* /var/msgs
* /var/preserve