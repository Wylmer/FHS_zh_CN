## 用途

`/usr`是文件系统中的第二个重要的部分。`/usr`是可共享的只读数据。就是说`/usr`应该可以在各种FHS兼容的主机之间共享并且禁止写入。任何主机特有的信息或随时间变化的量都保存在其他地方。
大型的软件包禁止在`/usr`层次结构中使用直接的子文件夹。