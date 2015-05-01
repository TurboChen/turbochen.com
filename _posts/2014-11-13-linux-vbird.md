---
title: "鸟哥的Linux私房菜（笔记）"
layout: post
category: [linux,notes]
tags: [linux, command, centos, vbird, notebook]
---

## 第七章 Linux文件与目录管理

### **pwd** （print work directory）显示目前所在的目录

* `-P` 取得正确的目录名称，而不是以连接文件的路径来显示

### **cd**(change directory) 切换目录

* **~** 表示用户的主文件夹，即`/home/username`
* **-** 回到切换目录之前的目录，重复使用将会在两个目录间来回切换

### **mkdir**(make directory) 新建目录

* `-m` 强制设置属性

> 若不使用`-m`则使用默认属性（默认属性可使用`umask`来查看）

### **rmdir**(remove directory) 移除目录

* `-p` 连同上层的“空的”目录也一起删除

> 如果要将目录下的所有东西删除可以使用`rm -r <directory>`

### **ls**(list) 查看文件与目录

|**ls** [-aAdfFhilnrRSt] directory|
|**ls** [--color={never,auto,always}] directory|
|**ls** [--full-time] directory|

* `-a` 全部的文件，连同隐藏文件

* `-d` 仅列出目录本身，不列出目录内的数据

* `-F` 根据文件、目录等信息给予附加数据结构，例如：**\*** 代表可执行文件，**/** 代表目录，**=** 代表socket文件，**\|** 代表FIFO文件

* `-l` 列出长数据串，包含文件的属性与权限等数据

* `-R` 连同子目录内容一起列出来

* `-S` 以文件容量大小排序

* `-t` 以时间排序

* `--full-time` 以完整时间模式（包含年、月、日、时、分）输出

* `--time={atime,ctime}` 输出访问时间或改变权限属性时间（ctime）而非内容更改时间（modification time）

### **cp** （copy）复制

|**cp** [-adfilprsu] source destination|
|**cp** [options] source1 source2 source3 ... directory|

> 在默认的条件中，cp的源文件与目的文件的权限是不同的，目的文件的所有者通常会是命令操作者本身

> 若源文件有两个以上，最后一个目的的目录必须是“目录”才行

* `-a` <u>相当于`-pdr`的意思</u>

* `-d` 若源文件为连接文件的属性（link file），则复制连接文件属性而非文件本身

* `-f` 为强制（force）的意思，若目标文件已经存在且无法开启，则删除后再尝试一次

* `-i` <u>若目标文件（destination）已经存在时，在覆盖时会询问操作的进行</u>

* `-l` 进行硬连接（hard link）的连接文件创建，而非复制文件本身

* `-p` 连同文件的属性一起复制过去，而非使用默认属性（备份常用）

* `-r` <u>递归持续复制</u>

* `-s` 复制成为符号连接文件（symbolic link），即“快捷方式”文件

* `-u` 若destination比source旧才更新destination

### **rm** （remove）移除文件或目录

|**rm** [-fir] 文件或目录|

* `-f` 就是force的意思，忽略不存在的文件，不会出现警告信息

* `-i` 互动模式，在删除前会询问用户是否操作

* `-r` 递归删除，最常用在目录的删除。<u>这是非常危险的参数！！！</u>

	[terry@laptop ~]$ rm ./-text- #删除一个带有 - 开头的文件，因为 - 是参数

### **mv** （move）移动文件与目录，或更名

|**mv** [-fiu] source destination|
|**mv** [options] source1 source2 source3 ... directory|

* `-f` 就是force的意思，忽略不存在的文件，不会出现警告信息

* `-i` 若目标文件（destination）存在时，就会询问是否覆盖

* `-u` 若目标文件已经存在，且source比较新，才会更新（update）

> 如果有多个源文件或目录，则最后一个目标文件一定是“目录”

### 取得路径的文件名与目录名称

	[terry@laptop ~]$ basename /etc/sysconfig/network
	network
	[terry@laptop ~]$ dirname /etc/sysconfig/network
	/etc/sysconfig

### **cat** （concatenate）直接查看文件内容

|**cat** [-AbEnTv]|

* `-A` 相当于`-vET`的整合参数，可列出一些特殊字符，而不是空白而已

* `-b` 列出行号，仅针对非空白做行号显示，空白行不标行号

* `-E` 将结尾的断行字符$显示出来

* `-n` <u>打印出行号，连同空白行</u>

* `-T` 将**[Tab]**按键以**^T**显示出来

* `-v` 列出一些看不出来的特殊字符

### **tac** 反向列式

> 由最后一行到第一行反向在屏幕上显示出来（和cat相反）

### **nl** 添加行号打印

|**nl** [-bnw]|

* `-b` 指定行号指定的方式，主要有两种

	* `-b -a` 表示不论是否为空行，也同样列出行号（类似 `cat -n` ）

	* `-b -t` 如果有空行，空的那一行不要列出行号（默认值）

* `-n` 列出行号表示的方法，主要有三种

	* `-n ln` 行号在屏幕的最左方显示

	* `-n rn` 行号在自己字段的最右方显示，且不加0

	* `-n rz` 行号在自己字段的最右方显示，且加0

* `-w` 行号字段占用的位数

	[terry@laptop ~]$ nl -b a -n rz /etc/issue #默认字段是6位数
	000001	\S
	000002	Kernel \r on an \m
	000003
	[terry@laptop ~]$ nl -b a -n rz -w 3 /etc/issue #改为显示三位数
	001	\S
	002	Kernel \r on an \m
	003

### **more** 翻页查看

|**more** directory|

* `空格键（Space）` 代表向下翻一页

* `Enter` 代表向下滚动一行

* `/字符串` 代表在这个显示的内容当中，向下查询“字符串”这个关键字

* `:f` 立即显示出文件名以及目前显示的行数

* `q` 代表立刻离开more，就是退出的意思

* `b` 或 `[Ctrl+b]` 代表往回翻页，只对文件有用，对管道无用

### **less** 翻页查看

|**less** directory|

* `空格键（Space）` 向下翻动一页
* `PageDown` 向下翻动一页
* `PageUp` 向上翻动一页
* `/字符串` 向下查询“字符串”
* `?字符串` 向上查询“字符串”
* `n` 重复前一个查询
* `N` 反向重复前一个查询
* `q` 退出less程序

### **head** 取出前面几行

|**head** [-n number] file|

* `-n` 后面接数字，代表显示几行的意思

### **tail** 取出后面几行

|**tail** [-n number][-f] file|

* `-n` 后面接数字，表示显示几行的意思
* `-f` 表示持续检测后面所接的文件名，要等到按下[Ctrl+C]才会结束tail的检测

> 默认情况下，显示最后的10行

	# 如果想要显示/etc/man.config中的地11到20行
	[terry@laptop ~]$ head -n 20 /etc/man.config |tail -n 10

### **od** 非纯文本文件

|**od** [-t TYPE] file|

* `-t` 后面可以接各种“类型（TYPE）”的输出，例如

	* `a` 利用默认的字符来输出

	* `c` 利用ASCII字符来输出

	* `d[size]` 利用十进制（decimal）来输出数据，每个整数占用size bytes

	* `f[size]` 利用浮点数（floating）来输出数据，每个数占用size bytes

	* `o[size]` 利用八进制（octal）来输出数据，每个整数占用size bytes

	* `x[size]` 利用十六进制（hexadecimal）来输出数据，每个整数占用size bytes

### **touch** 修改文件时间或创建新文件

**modification time (mtime)**：当该文件的“内容数据”更改时，就会更新这个时间。内容数据指的是文件的内容，而不是文件的属性或权限

**status time (ctime)**：当该文件的“状态”（status）改变时，就会更新这个时间，举例来说，像是权限与属性被更改了，都会更新这个时间

**access time (atime)**：当“该文件的内容被取用”时，就会更新这个读取时间（access），举例来说，我们使用cat去读取/etc/man.config，就会更新该文件的atime了

> 在默认情况下，ls显示出来的是该文件的mtime，也就是这个文件的内容上次被更改的时间

|**touch** [acdmt] file|

* `-a` 仅修改访问时间

* `-c` 仅修改文件的时间，若该文件不存在则不创建新文件

* `-d` 后面可以接欲修改的时间而不用目前的日期，也可以使用`--date="日期或时间"`

* `-m` 仅修改mtime

* `-t` 后面可以接欲修改的时间而不用目前的时间，格式为[YYMMDDhhmm]

<pre>
[terry@laptop ~]$ touch -d "2 days ago" bashrc #将bashrc的日期调整为两天前
[terry@laptop ~]$ touch -t 0809151314 bashrc #将bashrc的日期改为2008/09/15 13:14
</pre>

### **umask** 文件默认权限

> 显示的是需要减掉的权限

	[terry@laptop ~]# umask
	0022	#与一般权限有关的是后面三个数字
	[terry@laptop ~]# umask -S # -s (Symbolic)
	u=rwx,g=rx,o=rx

新建文件时：（-rw-rw-rw-） - （-----w--w-） =>> -rw-r--r--

新建目录时：（drwxrwxrwx） - （d----w--w-） =>> drwxr-xr-x

	[terry@laptop ~]$ umask 002 #设置umask的值为002

### **chattr** 设置文件的隐藏属性

|chattr [+-=] [ASacdistu] 文件或目录名称|

* `+` 增加某一个特殊参数，其他原本存在参数则不动

* `-` 删除某一个特殊参数，其他原本存在参数则不动

* `=` 仅有后面接的参数

* `A` 当设置了这个属性时，若你有访问此文件（或目录）时，他的访问时间atime将不会被修改，可避免I/O较慢的机器过度访问磁盘。这对速度较慢的计算机有帮助

* `S` 一般文件是异步写入磁盘的，如果加上S这个属性时，当你进行任何文件的修改，该改动会“同步”写入磁盘中

* `a` <u>当设置a后，这个文件将只能增加数据，而不能删除也不能修改数据，只有root才能设置这个属性</u>

* `c` 这个属性设置之后，将会自动将此文件压缩，在读取的时候将会自动解压缩，但是在存储的时候，将会先进性压缩后再存储（对大文件有用哟）

* `d` 当dump程序被执行的时候，设置d属性将可使该文件（或目录）不会被dump备份

* `i` <u>鸟哥说很厉害哟，它可以让一个文件“不能被删除、改名、设置连接，无法写入或添加数据”，对于系统安全性有相当大的帮助。只有root能设置此属性</u>

* `s` 当文件设置了s属性时，如果这个文件被删除，它将会被完全从这个硬盘空间中删除

* `u` 与s相反，当使用u来配置文件时，如果该文件被删除了，则数据内容其实还存在磁盘中，可以使用来找回该文件

### **lsattr** 显示文件隐藏属性

|**lsattr** [-adR] 文件或目录|

* `-a` 将隐藏文件的属性也秀出来

* `-d` 如果接的是目录，仅列出目录本身的属性而非目录内的文件名

* `-R` 连同子目录的数据也一并列出来

### 文件特殊权限：**SUID SGID SBIT**

-rw`x`r-`x`r-`x`

* **SetUID** （`s`标志在**文件所有者**的`x`项目为SUID）

	* SUID权限仅对二进制程序（binary program）有效

	* 执行者对于该程序需要具有x的可执行权限

	* 本权限仅在执行该程序的过程中（run-time）有效

	* 执行者将具有该程序所有者（owner）的权限

	* SUID仅可用在二进制程序上，不能够用在shell script上面

* **SetGID** （`s`标志在**用户组**的`x`项目为SGID）

	* 对文件来说：

		* SGID对二进制程序有用
		* 程序执行者对于该程序来说，需具备x的权限
		* 执行者在执行的过程中还会获得该程序用户组的支持

	* 对于目录来说：

		* 用户若对于此目录具有r与x的权限时，该用户能够进入此目录
		* 用户在此目录下的有效用户组（effective group）将会变成该目录的用户组
		* 若用户在此目录下具有w的权限（可以新建文件），则用户所创建的新文件的用户组与此目录的用户组相同

* **SBIT** (Sticky Bit)

	* 只针对目录有效
	* 当用户对于此目录具有w，x权限（可能是属于用户组或者其他人），即具有写入的权限时，当用户在该目录下创建文件或目录时，仅有自己与root才有权利删除该文件（或目录）（也就是说在group这个组里的人只能各自管理自己所创建的文件或文件夹）

* SUID/SGID/SBIT 权限设置

	* 4 为SUID
	* 2 为SGID
	* 1 为SBIT

<pre>
[terry@laptop ~]# chmod 4755 filename #将一个文件权限改为“-rwsr-xr-x”
[terry@laptop ~]# chmod u=rwxs, go=rx filename #或者是这样
# SUID: u+s
# SGID: g+s
# SBIT: o+t

#在当一个文件没有x的权限时，在相应的位置上，s和t会以大写“S和T”的样子出现
</pre>

### **file** 查看文件类型

|**file** filename|

### **which** 脚本文件名的查询

|**which** [-a] command|

* `-a` 将所有由PATH目录中可以找到的命令均列出，而不只第一个被找到的命令名称

### **whereis** 文件名的查找 寻找特定文件

|**whereis** [-bmsu] 文件或目录名|

* `-b` 只找二进制格式的文件

* `-m` 只找在说明文件manual路径下的文件

* `-s` 只找source文件

* `-u` 查找不在上述三个选项当中的其他特殊文件

### **locate** 文件名的查找

|**locate** [-ir] keyword|

* `-i` 忽略大小写的差异

* `-r` 后面可接正则表达式的显示方式

> locate寻找的数据是由**已创建的数据库/var/lib/mlocate**里面的数据所查找的
> 可以用`updatedb`来更新数据库

|**update**|根据/etc/updatedb.conf的设置去查找系统硬盘内的文件名，并更新/var/lib/mlocate内的数据文件|
|**locate**|根据/var/lib/mlocate内的数据库记载，找出用户输入的关键字文件名|

### **find** 文件名的查找

|**find** [PATH] [option] [action]|

* **与时间有关的参数** 共有-atime，-ctime，-mtime，下面以-mtime说明

	* `-mtime n` n为数字，意义为在n天之前的“一天之内”被更改过的文件

	* `-mtime +n` 列出在n天之前（不含n天本身）被更改过的文件名

	* `-mtime -n` 列出在n天之内（含n天本身）被更改过的文件名

	* `-newer file` file为一个存在的文件，列出比file还要新的文件名

<pre>
[terry@laptop ~]$ find / -mtime 0 #将过去系统上24小时内有改动的文件列出

[terry@laptop ~]$ find /etc -newer /etc/passwd #寻找/etc下面的文件，如果文件日期比/etc/passwd新就列出，-newer用在分辨两个文件之间的新旧关系是很有用的！

[terry@laptop ~]$ find /var -mtime -4 #找出“4天内被改动过的文件名”
[terry@laptop ~]$ find /var -mtime 4 #“4天前的那一天”
</pre>

+4代表大于等于5天前的文件名

-4代表小于等于4天内的文件名

4则是代表4~5那一天的文件名

* **与用户或用户组名有关的参数**

	* `-uid n` n为数字，这个数字是用户的账号ID，即UID，它是记录在/etc/passwd里面与账号名称对应的数字
	
	* `-gid n` n为数字，这个数字是用户组名的ID，即GID，它是记录在/etc/group中的
	
	* `-user name` name为账户名称，例如terry
	
	* `group name` name为用户组名，例如users
	
	* `-nouser` 寻找文件的所有者不存在于/etc/passwd中的人
	
	* `-nogroup` 寻找文件的所有用户组不存在于/etc/group中的文件

<pre>
[terry@laptop ~]$ find / -nouser #查找系统中不属于任何人的文件
</pre>

* **与文件权限及名称有关的参数**

	* `-name filename` 查找文件名为filename的文件

	* `-size [+-]SIZE` 查找比SIZE还要大（+）或小（-）的文件，这个SIZE的规格有：`c 代表byte`，`k 代表1024byete`
	
	* `-type TYPE` 查找文件的类型为TYPE的，类型主要有：一般正规文件（f）、设备文件（b，c）、目录（d）、连接文件（l）、socket（s）及FIFO（p）等属性
	
	* `-perm mode` 查找文件权限“刚好等于”mode的文件，这个mode为类似chmod的属性
	
	* `perm -mode` 查找文件权限“必须要全部包括mode的权限”的文件
	
	* `perm +mode` 查找文件权限“包含任一mode的权限”的文件

<pre>
[terry@laptop ~]$ find / -name passwd #找出文件名为passwd的这个文件
[terry@laptop ~]$ find / -perm +7000 #找出文件当中含有SGID或SUID或SBIT的属性
</pre>

> find会自己查找子目录

* **其他可进行的操作**

	* `-exec command` command为其他命令，-exec后面可再接其他的命令来处理查找到的结果

	* `-print` 将结果打印到屏幕上，它是默认操作

<pre>
[terry@laptop ~]$ find / -perm +7000 -exec ls -l {} \;
#将找到的文件使用ls -l列出来，-exec后面的ls -l就是额外的命令，命令不支持命令别名。{} 代表“由find找到的内容”，因为 ; 在bash环境下有特殊意义，因此要用反斜杠来转义

[terry@laptop ~]$ find /etc -name '*httpd*' #找出/etc下，文件名包含httpd的文件
</pre>

> Reference:《鸟哥的Linux私房菜》第三版
