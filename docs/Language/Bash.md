---
title: Bash
tags:
  - [Linux]
categories: [Linux]
date: 2020-04-28 11:00:14
---
<font face="微软雅黑"></font>
<center> </center>

<!-- more -->
[Quick Reference](https://quickref.me/)

[ShellGuide](https://github.com/qinjx/30min_guides/blob/master/shell.md)
[Learn bash in Y minutes](https://learnxinyminutes.com/docs/bash/)
[pure-bash-bible](https://github.com/dylanaraps/pure-bash-bible)

[重定向输入输出](https://segmentfault.com/a/1190000022100439)

# Shell 简介

shell是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。Ken Thompson的sh是第一种Unix Shell，Windows Explorer是一个典型的图形界面Shell。
Bourne Again Shell（/bin/bash） 最常用。

它不仅是一个功能强大的命令行接口,也是一个脚本语言解释器。我们将会看到， 大多数能够在命令行中完成的任务也能够用脚本来实现，同样地，大多数能用脚本实现的操作也能够在命令行中完成。

```
#!/bin/bash
cd ~
mkdir shell_tut
cd shell_tut

for ((i=0; i<10; i++)); do
    touch test_$i.txt
done

```
## 运行Shell脚本

1. 作为可执行程序

    chmod +x test.sh
    ./test.sh

2. 作为解释器参数
这种运行方式是，直接运行解释器，其参数就是shell脚本的文件名，如：

    /bin/sh test.sh
    /bin/php test.php

这种方式运行的脚本，不需要在第一行指定解释器信息，写了也没用。

    常见的解释型语言都是可以用作脚本编程的，如：Perl、Tcl、Python、PHP、Ruby。
编译型语言，只要有解释器，也可以用作脚本编程，如C shell是内置的（/bin/csh），Java有第三方解释器Jshell，Ada有收费的解释器AdaScript。
如下是一个PHP Shell Script示例（假设文件名叫test.php）：

    #!/usr/bin/php
    <?php
    for ($i=0; $i < 10; $i++)
            echo $i . "\n";

执行：

    /usr/bin/php test.php
或者：

    chmod +x test.php
    ./test.php

***
# shell语法


# 文件描述符
表述指向文件的引用。ANSI C中为 使用FILE结构体的指针。
与shell输入输出、文件读、文件写等绑定。

## 基本用法

命令 | 说明
---|---
command > file | 将输出重定向到 file。
command < file | 将输入重定向到 file。
command >> file | 将输出以追加的方式重定向到 file。
n > file | 将文件描述符为 n 的文件重定向到 file。
n >> file | 将文件描述符为 n 的文件以追加的方式重定向到 file。
n >& m | 将输出文件 m 和 n 合并。
n <& m | 将输入文件 m 和 n 合并。
<< tag | 将开始标记 tag 和结束标记 tag 之间的内容作为输入。

0 是标准输入（STDIN），1 是标准输出（STDOUT），2 是标准错误输出（STDERR）。
这里的 2 和 > 之间不可以有空格，2> 是一体的时候才表示错误输出。

## 重定向
在执行一个命令之前，可以使用重定向操作符对该命令的输入、输出进行重定向。

重定向可以修改文件描述符对应的文件，从而在读写同一个文件描述符时，可以读写到其他文件。

重定向输入会把指定的文件描述符关联到以读模式打开的文件。那么读取指定文件描述符，就会读取文件内容。

重定向输出会把指定的文件描述符关联到以写模式打开的文件。那么写入内容到指定文件描述符，就会写入文件。

在重定向之前，指定的文件描述符对应一个已经打开的文件。
重定向之后，该文件描述符会对应另一个文件、或者对应另一个文件描述符。而另一个文件描述符也是对应另一个已经打开的文件。

当下面文件名用于重定向时，bash 会进行特殊处理：

```
/dev/fd/fd：如果 fd 是一个已经打开的文件描述符整数值，则 /dev/fd/fd 文件会复制到文件描述符 fd
/dev/stdin：复制到文件描述符 0，也可以写为 /dev/fd/0。文件描述符 0 一般对应标准输入
/dev/stdout：复制到文件描述符 1，也可以写为 /dev/fd/1。文件描述符 1 一般对应标准输入
/dev/stderr：复制到文件描述符 2，也可以写为 /dev/fd/2。文件描述符 2 一般对应标准错误输出
```