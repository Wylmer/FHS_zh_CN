## /var/log：日志文件和文件夹

### 5.10.1. 用途

此文件夹中包含各种日志文件。绝大多数的日志应该写入此文件夹或其中某个相应的子文件夹。

### 5.10.2. 特殊选项

如果安装了相应的子系统，`/var/log`中必须有以下文件或符号链接：

文件	|描述
--------|-----------------------------------
lastlog	|每位用户上次登录的记录
messages	|Syslogd产生的系统消息
wtmp	|所有登录和注销的记录
