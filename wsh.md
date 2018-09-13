## WSH {#wsh}

Windows脚本有着一个非常坚实的基础，那就是Windows脚本的运行环境--Windows脚本宿主(Windows scr Host) ，简称WSH。它是一个Windows管理工具，能够给VBscr 、Javascr 等脚本文件提供一个特殊的外部运行环境，换言之，当我们运行某个VBS文件时，是WHS在幕后为之创建对象(也就是功能模块，比如:读写注册表、操作文件、创建快捷方式等)，并且按照脚本内的语言的指令执行操作。

小提示

WSH即可以使脚本直接在Windows下，也可以让其运行在命令提示符下，它在Windows中的程序名为Wscr ，在命令提示下的程序名为Cscr 。