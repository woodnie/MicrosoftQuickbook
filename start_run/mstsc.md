### mstsc {#mstsc}

mstsc (Microsoft terminal services client)

　　创建与终端服务器或其他远程计算机的连接，编辑现有&quot;远程桌面连接 (.rdp)&quot;配置文件，并将 Windows XP 连接（使用&quot;客户端国防部设备 接管理器&quot;创建的连接）迁移到新的 .rdp 文件中。

编辑本段语法

　　mstsc.exe {ConnectionFile|/v:server} [/console] [/f] [/w:width /h:height]

　　mstsc.exe /edit&quot;ConnectionFile&quot;

　　mstsc.exe /migrate

编辑本段参数

　　ConnectionFile 指定用于连接的 .rdp 文件的名称

　　/v:server[;port] 指定要连接的远程计算机

　　/admin 将连接到会话以管理服务器

　　/f 在全屏幕模式下启动&quot;远程桌面&quot;连接

　　/w:width 指定远程桌面窗口的宽度

　　/h:height 指定远程桌面窗口的高度

　　/public 在公用模式下运行远程桌面

　　/span 是远程计算机的高度和宽度与本地虚拟桌面相匹配，如有必要扩展到多个显示器。若要扩展到多个显示器，所有显示必须具有相同的高度并垂直排列

　　/console 连接到指定 Windows 2000 Server 的控制台会话

　　/edit 打开指定的 .rdp 文件进行编辑

　　/migrate 将使用&quot;客户端连接管理器&quot;创建的旧版连接文件迁移到新的 .rdp 连接文件中

编辑本段注释

　　您必须是要连接的服务器上的管理员才能创建远程控制台连接。

　　对于每个用户来说，.rdp 文件在&quot;我的文档&quot;中是作为隐藏文件存储的。

　　mstsc 与远程客户端之间是用Microsoft的远程桌面协议(Remote Desktop Protocol，简称RDP) 连接的,而windows xp的rdp有1个并发数的连接限制。

++++++++++++++++++++++++

在登陆上服务器之后，打开我的电脑，在地址栏中输入&quot; \\tsclient\d\ &quot;(不包括引号)

[http://server.it168.com/server/2007-10-15/200710150828937.shtml](http://server.it168.com/server/2007-10-15/200710150828937.shtml) ?

++++++++++++++++++++++++

考虑到服务器都是通过Windows 终端服务器来管理的，就想办法对其登录做个监控，找了个命令行下发邮件的小工具blat还有批处理，做了个简单的监控程序，功能是当有人通过终端登录且成功后，会向指定的邮箱发送登录者IP地址。

1.先下载blat解压缩到c盘blat目录下面。

2.任意目录新建一个bat文件，我这里是mail.bat,内容如下，

@echo off

date /t &gt;mail.txt

time /t &gt;&gt;mail.txt

netstat -n -p tcp | find &quot;3389&quot; &gt;&gt;mail.txt

:::::::::::::: config::::::::::::::

set from=7263974@qq.com

set user=neeao.com

set pass=neeao.com

set to=xxxxx@qq.com

set subj=3389

set mail=mail.txt

set server=smtp.126.com

set debug=-debug -log blat.log -timestamp

::::::::::::::::: run blat :::::::::::::::::

C:\blat\full\blat.exe %mail% -to %to% -base64 -charset Gb2312 -subject %subj% -server %server% -f %from% -u %user% -pw %pass% %debug%

start Explorer

很简单的了，先通过bat查找哪个ip连接到了本机的3389端口，然后邮件发送到指定邮箱。

3.进入控制面板---管理工具---终端服务器配置---RDP-Tcp---属性-环境-用户登录时启用下列程序---在程序路径和文件名---写&quot;C:\mail.bat&quot;---起始于---写&quot;C:\&quot;这样就ok了。

4.注销，重新登录，看是否能收到邮件。如果出错的话，桌面出不来的话，可通过ctrl+alt+end来呼出任务管理器来调用桌面。

5.目前发现个小bug，就是登录的时候，会弹出一个cmd的框。

6.如果开通邮箱的短信通知，或者使用139的邮箱，可以达到实时的手机短信通知，有兴趣的可以试试