# **群组的管理和文件权限管理**

## **群组管理的命令**

Linux 中每一个用户都属于一个特定的群组，如果不设置用户的群组，默认会创建一个和它的用户名一样的群组，并且把用户划归到这个群组

1.**groupadd：创建群组**

groupadd friends ，创建一个名为 friends 的群组

# 文本编辑器

## Nano

## Nano基础概念

Nano 是一个文本编辑器，不是文本处理器

1.**文本编辑器**：可以编辑和查看文本文件,但是不能对文字做格式处理,例如：加粗，斜体，改变颜色，改变字体大小，添加超链接等等。

2.**文本处理器**：又叫文档编辑器，不仅可以编辑和查看文档，而且可以对其文字进行格式处理，加下划线，设为标题，插入图片等等。

3.在CentOs中，，要启动 nano，只需要在终端中输入 **nano** ， 回车，就打开了 nano 文本编辑器，可以直接在里面编辑文字。

### Nano中的快捷键

Ctrl+X 标明的是 Exit，就是 退出Nano

Ctrl+G：显示帮助文档

Ctrl+O：保存文件

Ctrl+R：打开其他文件

Ctrl+Y：上一个屏幕

Ctrl+V：下一个屏幕（PaUp 和 PaDn也可以转换屏幕）

Ctrl+K：剪切当前一行

Ctrl+X：退出

Ctrl+W：查找

Ctrl+U：粘贴刚剪切的内容

Ctrl+\：替换

Ctrl+F：向前移动一格光标

Ctrl+B：向后移动一格光标

Ctrl+P：向上移动一行

Ctrl+N：向下移动一行

不需要下方的帮助文档：先按 Esc 键，再按 X 键，帮助文档就没了，如果要重新调出帮助文档，则同样操作。

### Nano中的参数

1.nano file.txt：用 nano 打开 file.txt，如果file.txt存在且你有写的权限那你就可以用 nano 来修改这个文件了，如果 file.txt 文件不存在，就会创建一个空文件，名字叫做 file.txt。

2.-m：激活鼠标，加了 -m 参数鼠标可以通过点击来控制光标的位置。

3.-i：激活自动缩进的功能。

4.-A：激活智能 Home 键的功能，按下 Home 键它会智能地判断，根据一行的开始处有无缩进来跳

5.nano -miA file.txt：同时激活三个属性。

### **通过 .nanorc 来配置 Nano**

1.用ls -l命令是列不出来的，需要用ls -a来列出

2.每次 nano 启动前，它会读取此配置文件，而bashrc 是当 Linux 的 Bash shell 启动后所运行的脚本

3.路径：/home/oscar/.nanorc 如果在家目录没有 .nanorc ，那么 nano 会用全局的配置文件

4.配置语句是以 set 或 unset 开头,

如：set mouse ，激活鼠标，就不用每次nano激活都用-m参数

set autoindent ：激活自动缩进，相当于 -i 参数的作用

set smarthome ：激活智能 Home 键,相当于 -A参数的作用

保存文件：Ctrl+O

退出 nano ：Ctrl+X 

5.全局配置文件

nano 有一个全局的配置文件，是为系统上所有用户所公共调用的，也叫 nanorc，在/etc/nanorc目录下，只能被 root 用户修改，修改这个文件，用 sudo 命令：sudo nano /etc/nanorc

### **通过 .bashrc 配置终端**

1.对于终端，也有一个配置文件，叫做 .bashrc ，是用户的终端配置文件。一般位于 /home/oscar/.bashrc，打开家目录下的终端配置文件，即输入：nano ~/.bashrc，终端的 bash 也有它的全局配置文件：/etc/bashrc，家目录下的 .bashrc 文件的优先级比系统的/etc/bashrc文件高。

# 软件包

### 切换centOS的软件源

1.package：包。这是软件的二进制安装包，类似 Windows 中软件的安装程序

2.repository：仓库，软件的仓库，就是存放软件的服务器，一般从这上面下载软件

3.dependency：依赖， 一个软件包可能需要其他的软件包作为运行的基础

### 包管理工具;yum

yum：终端的软件包管理命令一般用 yum

1.**更新软件包**：sudo yum update / upgrade

2.**搜索软件包**：sudo yum search

3.**安装软件包**：sudo yum install xxx ，xxx 是对应软件包名

4.**删除软件**：sudo yum remove xxx 或者 sudo yum autoremove xxx，xxx 是对应软件包名

5.本地的 .rpm 软件包，可以用rpm、yum安装

sudo rpm -i *.rpm ，用于安装，sudo rpm -e 包名 ，用于卸载；

sudo yum localinstall *.rpm，用于安装，sudo yum remove 包名，用于卸载。

# **RTFM**

## 命令

1.man 命令，显示使用手册，用于查看系统中自带的各种参考手册

如果 man 的手册没有安装，可以运行以下命令：sudo yum install -y man-pages

如果 man 的手册不全，可以运行以下命令：sudo mandb

输入 man + 数字 + 命令/函数，可以查到相关的命令和函数，若不加数字，man 默认从数字较小的手册中寻找相关命令和函数

2.在手册中移动

键盘上的方向键：向上和向下键使我们实现上一行和下一行的跳转

PgUp 和 PgDn（或者空格键）键：实现上一页和下一页的跳转

键盘上的 Home 和 End 键：实现开始和结尾的跳转

/ 键（斜杠）：实现搜索，和之前在 less 命令中功能类似

键盘上的 q 键：退出手册页

3.手册页的不同区域

NAME:手册页对应的命令或函数名字，后接简单描述

SYNOPSIS :使用此命令的所有方法

DESCRIPTION : 这个区域也会包括所有参数及其用法

4.创建目录

a.创建单个目录，makdir  directory

b.同时创建多个目录，例如：mkdir photo video music：创建 photo，video，music 三个目录

5.拷贝：cp file.jpg file_copy.jpg photo/ ，将 file.jpg 和 file_copy.jpg 两个文件拷贝到 photo 这个文件夹

6.apropos 命令：查找命令，可以在所有手册页中查找相关的命令

apropos sound：查找如何用终端的命令来控制音量，命令列出了所有使用手册中有 sound 这个关键字的命令，左侧是命令的名字，后边是命令的手册中出现关键字的句子

7.locate 命令：快速查找

locate renamed_file：查找一个叫做 renamed_file 的文件,locate 命令不会对你实际的整个硬盘进行查找,而是在文件的数据库里查找记录,刚创建不久的文件，因为它们还没被收录进文件数据库。因此 locate 命令就找不到其索引,我们需要手动更新数据库。

8.文件数据库

updatedb 命令强制系统立即更新文件数据库,updatedb 命令只能由 root 用户执行，locate 命令方便快捷，易于使用，locate 命令不能找到一天之内刚创建的文件，除非你先用 root 身份运行 updatedb 命令来更新文件数据库

9.find 命令:深入查找

find 命令不会在文件数据库中查找文件的记录,而是遍历你的实际硬盘

find -name "new_file" : -name 参数指定了文件名字，是 new_file

find /var/log -name "syslog" :在 /var/log 目录下查找名为syslog的文件,如果没有权限访问的目录，会显示“Permission denied”，切换成 root 后，就可以查找所有目录了，不会出现“权限被否决”

find /var -size +20G :表示查找大于 20Go 的文件,如果没有加减号，则查找大小等于指定数值的文件

find -name "*.jpg" -delete :会删除当前目录及其子目录下所有以 .jpg 为后缀的文件









