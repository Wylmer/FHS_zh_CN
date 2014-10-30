## /usr/local/share

对此文件夹下内容的要求同`/usr/share`。唯一追加的限定是`/usr/local/share/man`和`/usr/local/man`文件夹必须同步（通常意味着其中之一为符号链接）[^8]。

---
[^8]: `/usr/local/man`可能在将来的FHS版本中废弃，因此如果东西放哪都一样，将那个（`/usr/local/man`）做成符号链接比较明智。
