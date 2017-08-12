title: Linux命令man
date: 2017-08-12
tags:
 - Linux
---

在使用Linux命令的时候，我们都知道有个man命令来查看其他命令的文档。这里的man是manual的的简写。
当我们在命令行输入man date 命令就可以进入date的man page了。

```shell
DATE(1)                          User Commands                         DATE(1)

NAME
       date - print or set the system date and time

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

DESCRIPTION
       Display the current time in the given FORMAT, or set the system date.

       -d, --date=STRING
              display time described by STRING, not ‘now’

       -f, --file=DATEFILE
              like --date once for each line of DATEFILE
...


DATE STRING
       The --date=STRING is a mostly free format human readable date string such as "Sun, 29 Feb 2004 16:21:42 -0800" or "2004-02-29 16:21:42" or even "next Thursday".  A date string may contain items indicating cal-
       endar date, time of day, time zone, day of week, relative time, relative date, and numbers.  An empty string indicates the beginning of the day.  The date string format is more complex  than  is  easily  docu-
       mented here but is fully described in the info documentation.

ENVIRONMENT
       TZ     Specifies the timezone, unless overridden by command line parameters.  If neither is specified, the setting from /etc/localtime is used.

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       Report date bugs to bug-coreutils@gnu.org
       GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
       General help using GNU software: <http://www.gnu.org/gethelp/>
       Report date translation bugs to <http://translationproject.org/team/>

COPYRIGHT
       Copyright © 2010 Free Software Foundation, Inc.  License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
       This is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent permitted by law.

```


文档大概包含以下几个部分：


|    部分     |                           说明                            |
| ----------- | --------------------------------------------------------- |
| Name        | 简短的命令说明                                            |
| SYNOPSIS    | 概要 简单的命令执行语法介绍                               |
| DESCRIPTION | 完整的说明，命令使用的有些细节                            |
| OPTIONS     | 命令的一些选项说明，有些命令直接在DESCRIPTION包含了这部分 |
| COMMANDS    | 程序在执行的时候，可以在次程序中执行的命令                |
| FILES       | 程序涉及到文件                                            |
| SEE ALSO    | 命令或者数据的其他说明                                    |
| EXAMPLE     | 命令的一些参考例子                                        |
| BUGS        | 是否有相关的错误                                          |


这里列出的部分并不一定会出现所有的文档中，有些命令可以只有NAME和DESCRIPTION两部分，了解文档的大致结构可以帮助我们更
快速的检索我们需要的信息。

在查看文档时常用的按键

|   按键    |             说明             |
| --------- | ---------------------------- |
| 空格键    | 向下翻页                     |
| page up   | 向上翻页                     |
| page down | 向下翻页                     |
| home      | 转到第一页                   |
| end       | 转到最后一页                 |
| ／string  | 向下搜索字符串               |
| ?string   | 向上搜索字符串               |
| n,N       | n为下一个查询，N为上一个查询 |
| q         | 退出                             |


另外我们在进入man page的后发现命令后面都会有一个数字,比如下面的DATE(1)，那这些数字又代表什么意思呢？
具体的含义我们可以通过man man命令的MANUAL SECTIONS部分查看相关信息
```shell

MANUAL SECTIONS
       The standard sections of the manual include:
       1      User Commands //用户命令

       2      System Calls //系统调用

       3      C Library Functions //C语言的函数库

       4      Devices and Special Files //设备和特殊的文件

       5      File Formats and Conventions //文件的格式也一些约定

       6      Games et. Al.  //游戏等

       7      Miscellanea //杂集

       8      System Administration tools and Deamons //系统管理员工具
       Distributions customize the manual section to their specifics, which often include additional sections.
```

通过man命令查询的信息，存放在/usr/share/man目录下，目录中有各种语言版本的man文件。另外在/usr/share/doc/也存放来很多有用的文档值得我们来挖掘。比如我们经常用到的init脚本就可以在/usr/share/doc/initscripts-xxxx下找到相关的说明文件sysvinitfiles
