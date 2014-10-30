## 4.11. /usr/share：与架构独立的数据

### 4.11.1. 用途

`/usr/share`层次结构用于所有只读的与架构独立的数据文件[^10]。

这一层次结构应该可以在给定操作系统的所有架构平台之间共享；因而，例如对i386、Alpha和PPC平台的站点可以维护一个集中挂载的`/usr/share`文件夹。不过注意，一般不应该在不同的操作系统间或相同操作系统的不同版本间共享`/usr/share`。

任何包含或要求不需要修改数据的程序或软件包应该将这些数据保存在`/usr/share`（或`/usr/local/share`，本地安装时）下。建议使用`/usr/share`下的一个子文件夹来放置它们。

在`/usr/share/games`下的游戏数据应该是纯静态的数据。任何可修改的文件如分数文件、游戏日志之类，应该放置在`/var/games`中。

### 4.11.2. 要求

`/usr/share`下必须有如下文件夹或符号链接：

文件夹	|描述
--------|----------------------------
man	|在线手册
misc	|各种与架构独立的数据

### 4.11.3. 特殊选项

如果安装了相应子系统，则`/usr/share`中必须有以下文件夹或符号链接：

文件夹	|描述
--------|--------------------------------------------
dict	|单词列表（可选）
doc	|各种文档（可选）
games	|`/usr/games`的静态数据文件（可选）
info	|GNU Info系统的主文件夹（可选）
locale	|区域信息（可选）
nls	|本地语言支持的消息索引（可选）
sgml	|SGML数据（可选）
terminfo	|Terminfo数据库的文件夹（可选）
tmac	|未使用`groff`发布的`troff`宏（可选）
xml	|XMl数据（可选）
zoneinfo	|时区信息和配置（可选）

建议程序特定的、与架构独立的文件夹放在这里。这些文件夹包括`groff`、`perl`、`ghostscript`、`texmf`和`kbd`（Linux）或`syscons`（BSD）。然而也可以将它们放在`/usr/lib`中以保持向后兼容，这由发行者确定。类似的，如果发行者想要放置游戏数据，也可以在`/usr/share/games`层次结构之外使用`/usr/lib/games`层次结构。

### 4.11.4. /usr/share/dict：单词表（可选）

#### 4.11.4.1. 用途

此文件夹是放系统单词表的地方。传统上这一文件夹只包含英语words文件，它用于`look`(1)和各种拼写程序。Words可以使用美式或英式拼写。

> #### 基础知识

> 只有单词表放在此处的原因是它们是所有拼写检查程序之间惟一通用的文件。

#### 4.11.4.2. 特殊选项

如果安装了相应子系统，`/usr/share/dict`下必须有以下文件或符号链接：
文件	|描述
--------|--------------------
words	英语单词表（可选）

同时需要英式和美式拼写的站点可以将`words`链接到`/usr/share/dict/american-english`或`/usr/share/dict/british-english`。

其他语言的单词表可以使用该语言的英文名称添加，例如，`/usr/share/dict/french`、`/usr/share/dict/danish`，等等。对有问题的语言，可能的话应该使用合适的ISO 8859字符集；如果可能，应该使用Latin1(ISO 8859-1)字符集（通常不适用）。

如果存在，这里可以包含其他单词表。

### 4.11.5. /usr/share/man：手册页

#### 4.11.5.1. 用途

本节细述整个系统中手册页的组织，包括`/usr/share/man`。也提到了`/var/cache/man`那一节。

系统中`<mandir>`的初始位置是`/usr/share/man`。`/usr/share/man`包含了`/`和`/usr`文件系统下命令和数据的手册信息[^11]。

手册页保存在`<mandir>/<locale>/man<section>/<arch>`中。对`<mandir>`、`<locale>`、`<section>`和`<arch>`的解释在下面给出。

下面是手册各节的描述：

* Man1：用户程序手册。本节中包含了描述公共访问的命令的手册页面。用户需要使用的绝大多数程序文档位于这里。
* Man2：系统调用。这一节描述了所有的系统调用（对内核执行操作的请求）。
* Man3：库函数和子例程。第3节描述了没有直接调用系统服务的程序库例程。这一节与第2节实际上只针对编辑者。
* Man4：特殊文件。第4节描述了系统中的特殊文件、有关的驱动功能和网络支持。典型的，这包括/dev下能找到的设备文件和内核对网络协议的支持接口。
* Man5：文件格式。很多数据文件格式的文档都在第5节。这包括各种头文件、程序输出文件和系统文件。
* Man6：游戏。这一节是游戏、演示和通常很琐碎的程序的文档。对这些内容的必要性，不同的人有不同的见解。
* Man7：各种难以归类的手册页划归第7节。Troff和其他文本处理宏包（的手册）放在这里。
* Man8：系统管理员用来进行系统操作和维护的系统管理程序的文档放在这里。有些程序有时也对普通用户有用。

#### 4.11.5.2. 特殊选项

`/usr/share/<mandir>/<locale>`下必须有以下文件夹或符号链接，除非它们是空的[^12]：

文件夹	|描述
--------|-----------------------
man1	|用户程序（可选）
man2	|系统调用（可选）
man3	|库调用（可选）
man4	|特殊文件（可选）
man5	|文件格式（可选）
man6    |游戏（可选）
man7    |杂项
man8	|系统管理（可选）

`<section>`部分描述了手册的节次。

必须在`/usr/share/man`下预设（子文件夹）来支持各种不同（或多种）语言的手册文件。这些预设必须考虑存储和手册间的相互引用。有关因素包括语言（包括地域差异）和字符编码。

`/usr/share/man`下语言子文件夹的命名基于附录E中的POSIX 1003.1标准，它描述了区域识别字符串——描述文化环境最被广泛接受的方法。`<locale>`字符串是：
`<language>[_<territory>][.<character-set>][,<version>]`

`<language>`字段必须取自ISO 639（代表语言名的一套代码）。它必须是两个字符宽且必须只能为小写。

`<territory>`字段必须是ISO 3166（代表国家的一种规定）中的双字符代码，如果里面有。（绝大多数人应该对电子邮件中使用的双字符国家代码比较熟悉。）它必须是两个字符宽，且只能为大写[^13]。

可以在`<character-set>`字段后放一个指定`<version>`（版本）的参数，用逗号分开。这可以用来区别各种不同的文化需要；例如，词典顺序对比一个更面向系统的整理顺序。本标准不推荐使用`<version>`字段，除非需要。

手册页使用单一语言和代码集的系统可以忽略`<locale>`子字符串并把所有手册页保存在`<mandir>`下。例如，只有以ASCII编码的英文手册页的系统可以将手册页（`man<section>`文件夹）直接保存在`/usr/share/man`下。（传统的环境中实际上就是这么安排的。）

对于有一套广泛接受字符编码集的国家，可以忽略`<character-set>`字段，但是强烈建议保存它，尤其是对于有数套相互冲突标准的国家。

各种例子：

语言Language	|地区Territory	|字符集Character set	|文件夹
----------------|---------------|-----------------------|--------------
英语	|——	|ASCII	|/usr/share/man/en
英语	|英国	|ISO 8859-15	|/usr/share/man/en_GB
英语	|美国	|ASCII	|/usr/share/man/en_US
法语	|加拿大	|ISO 8859-1	|/usr/share/man/fr_CA
法语	|法国	|ISO 8859-1	|/usr/share/man/fr_FR
德语	|德国	|ISO 646	|/usr/share/man/de_DE.646
德语	|德国	|ISO 6937	|/usr/share/man/de_DE.6937
德语	|德国	|ISO 8859-1	|/usr/share/man/de_DE.88591
德语	|瑞士	|ISO 646	|/usr/share/man/de_CH.646
日语	|日本	|JIS	|/usr/share/man/ja_JP.jis
日语	|日本	|SJIS	|/usr/share/man/ja_JP.sjis
日语	|日本	|UJIS(或EUC-J)	|/usr/share/man/ja_JP.ujis
*汉语*   |中国大陆   |UTF-8  |/usr/share/man/zh_CN
*汉语*   |中国台湾   |UTF-8  |/usr/share/man/zh_TW

> 译注：汉语是我加的。个人建议不要使用中文字符集，统一使用UTF-8。

类似的，为手册页所做的预设必须是独立于架构的，如设备驱动或系统管理命令的文档。这些必须安置在相应`man<section>`文件夹下的某个`<arch>`文件夹中；例如，i386架构的`ctrlaltdel`(8)命令的man页面可以放在`/usr/share/man/<locale>/man8/i386/ctrlaltdel.8`。

`/usr/local`下命令和数据的手册页保存在`/usr/local/man`下。X11R6的手册页保存在`/usr/X11R6/man`下。同理，系统中所有的手册页必须与`/usr/share/man`保持相同的结构。

包含格式化的手册页记录的cat页面的各节（`cat<section>`）也应位于`<mandir/<locale>`下，但不要求并且也不允许以nroff source手册页的lieu形式发布。

各节从“1”到“8”加序号的做法是按传统定义的。通常，位于特定节中的手册页文件名以`.<section>`结尾。

另外，一些应用程序特定的大型手册页文件名带有附加的后缀。MH邮件处理系统手册页必须在所有MH手册后加`mh`后缀。所有X窗口系统的手册页文件名后必须附加一个`x`。

`/usr/share/man`下存放各种语言的手册页到合适的子文件夹的做法也适用于其他的手册页层次结构，如`/usr/local/man`和`/usr/X11R6/man`。（这部分的标准也适用于后面可选的`/var/cache/man`结构那节。）

### 4.11.6. /usr/share/misc：各种独立于架构的数据
此文件夹包含了各种独立于架构的、不需要在/usr/share下单独开辟子文件夹的文件。

#### 4.11.6.1. 特殊选项
如果安装了相应子系统，则`/usr/share/misc`下必须有以下文件或符号链接：

文件	|描述
--------|--------------------------------------
ascii	|ASCII字符集表（可选）
magic	|文件命令用的魔数的默认列表（可选）
termcap	|终端功能数据库（可选）
termcap.db	|终端功能数据库（可选）

其他（应用程序特定的）文件也可以放在这里，但发行者可以酌情将它们放在`/usr/lib`/中[^14]。

### 4.11.7. /usr/share/sgml：SGML数据（可选）

#### 4.11.7.1. 用途

`/usr/share/sgml`包含了SGML应用程序使用的独立于架构的文件，如普通索引（不是集中索引，参见`/etc/sgml`），DTD、实体或样式表。

#### 4.11.7.2. 特殊选项

如果安装了相应子系统，则`/usr/share/sgml`中必须有以下文件夹或符号链接：

文件夹	|描述
--------|-----------------------
docbook	|Docbook DTD（可选）
tei	Tei |DTD（可选）
html	|Html DTD（可选）
mathml	|Mathml DTD（可选）

没有专门对应于给定DTD的其他文件可以放在它们自己的子文件夹中。

### 4.11.8. /usr/share/xml：XML数据（可选）

#### 4.11.8.1. 用途

`/usr/share/xml`包含XML应用程序使用的独立于架构的文件，如普通索引（不是集中索引，参见`/etc/sgml`），DTD、实体或样式表。

#### 4.11.8.2. 特殊选项

如果安装了相应子系统，`/usr/share/xml`下必须有以下文件夹或符号链接：

文件夹	|描述
--------|------------------------
docbook	|Docbook XML DTD（可选）
xhtml	|XHTML DTD（可选）
mathml	|MathML DTD（可选）

---
[^10]: 这种数据以前有很多存放在/usr（man、doc）或/usr/lib（dict、terminfo、zoneinfo）。
[^11]: 显然，`/`下没有手册文件，因为启动时不需要，而且实际上紧急情况下也用不着。
[^12]: 例如，如果`/usr/local/man`第4节（设备）中没有手册页，那么`/usr/local/man/man4`可以忽略。
[^13]: 很突出的一个例外就是对于英国的规则，在ISO 3166中是‘GB’，但绝大多数电子邮件地址中是‘UK’。
[^14]: 例如：`airport`、`birthtoken`、 `eqnchar`、`getopt`、`gprof.callg`、`gprof.flat`、`inter.phone`、`ipfw.samp`.`filters`、`ipfw.samp.scripts`、`keycap.pcvt`、`mail.help`,`mail.tildehelp`、`man.template`、`map3270`、`mdoc.template`、`more.help`、`na.Phone`、`nslookup.help`、`operator`、`scsi_modes`、`sendmail.hf`、`style`、`units.lib`、`vgrindefs`、`vgrindefs.db`、`zipcodes`等文件。

