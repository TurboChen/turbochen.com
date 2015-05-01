---
titile: "Shell脚本"
layout: post
category: [linux, reprint]
tags: [linux, shell]
---

### 通配符

* `*` 代表一个或多个字符 
* `?` 代表一个字符

### **|** 管道

* 把前面的命令运行的结果交给后面的命令

### 控制

* `[Ctrl+Z]` 暂停
* `[Ctrl+C]` 终止

### **env** 列出所有系统预设的系统变量

> 当前登陆的用户不同，结果也不同

* `set` 显示系统预设的变量 

### 变量

	echo $<变量名> #输出变量的值

* **PATH** 决定了shell将到哪些目录中寻找命令或程序
* **HOME** 当前用户主目录
* **HISTSIZE** 历史记录数
* **LOGNAME** 当前用户的登陆名
* **HOSTNAME** 当前的主机名
* **SHELL** 前用户Shell类型
* **LANG** 语言相关的环境变量，多语言可以修改此环境变量
* **MAIL** 当前用户的邮件存放目录
* **PWD** 当前目录

#### 自定义变量

	[terry@laptop ~]$ val=Apple
	[terry@laptop ~]$ echo $val
	Apple

> 现在这种变量只能在当前的shell中生效

* 想要系统内**所有用户**登陆后都能使用该变量：需要在`/etc/profile`文件末加入`export val=Apple`然后运行一下`source /etc/profile`

* 想要**当前用户**使用该变量：在用户主目录下的`.bashrc`文件最后加入`export val=Apple`然后运行`source.bashrc`

### **bash** 再打开一个shell

### **grep** 过滤一个或多个字符

	[terry@laptop ~]$ cat text |grep hello #将cat所得到的结果进行过滤，只显示和hello有关的内容


### **cut** 截取某个字段

* `-d` 后面跟分隔字符，分隔字符要用双引号括起来
* `-c` 后面接的是第几个字符，或者-c[n1]-[n2]
* `-f` 后面接的是第几个区块

### **sort** 排序

* `-t` 分隔符 ：作用跟cut的-d一个意思
* `-n` 使用纯数字排序
* `-r` 反向排序
* `-u` 去重复
* `-kn1,n2` 由n1区间排序到n2区间，可以只写-kn1，即对n1字段排序


### **wc** 统计文档的行、字符、单词个数

* `-l` 统计行数
* `-m` 统计字符数
* `-w` 统计词数

### **uniq** 过滤重复行

* `-c` 统计重复的行数，并把行数写在前面

### **tee** 类似重定向

> 与重定向不同的是会输出添加的内容

### **tr** 替换字符

* `-d` 删除某个字符，-d 后面跟要删除的字符
* `-s` 把重复的字符去掉

<pre>tr '[a-z]' '[A-Z]' #小写转为大写</pre>

### **split** 切割文档

* `-b` 依据大小来分割文档，单位为byte
* `-l` 依据行数来分割文档

### **;** 分号 运行多个命令

* 同时运行多个命令

### **&** 将命令放到后台执行

* `command [option] &`

> 通常用于非常耗时的命令

### **jobs** 查看当前shell中后台执行的任务

### **fg** 把后台的任务调到前台来执行

* `[Ctrl+Z]` 暂停任务，再使用`bg`可以再次进入后台执行
* `fg`后加上任务号来指定调到前台执行的任务，任务号可以用`jobs`命令得到

### **>** 重定向（取代）

> 会覆盖原有的内容

	[terry@laptop ~]$ echo "hi~" >text.txt
	[terry@laptop ~]$ cat text.txt
	hi~

### **\>\>** 追加重定向（追加）

> 就是追加的意思咯，不会改变原来的内容

### **2>** 错误重定向

> 只针对错误信息

### **2\>\>** 错误追加重定向

> 只针对错误的信息

### **[]** 中括号，中括号内为字符组合，代表字符组合中的任意一个

	ls test[a-c]
	testa	testb

	ls test[12a]
	testa

### **;** **&&** **||**

	command1; command2
	command1 && command2
	command1 || command2

* `;` command1和command2都会被执行
* `&&` 当command1执行成功才执行command2，否则不执行
* `||` 当command1执行成功，command2就不执行了（或者当command1执行不成功才执行command2）

### **!!** 再次执行上次的命令

* `!n` n是数字，表示执行命令的第n条命令
* `![string]` [string]是任意的字符，表示执行最近的以[string]开头的命令

### **alias** 别名

* `alias [命令的别名]=[\`具体的命令\`]` 设置别名
* `unalias` 用来解除别名

> Reference: http://www.92csz.com/study/linux/12.htm
