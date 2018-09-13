#### net {#net}

net

net user admin godmour /add 新建一个用户名为 admin 密码为 godmour 默认为user组成员

net user admin /del 将用户名为admin的用户删除

net user admin /active:no        将用户admin禁用

net user admin /active:yes 将用户admin激活

net user admin 查看拥护admin用户的情况

net user admin godmour         把admin的密码修改成 godmour

net share  #查看系统开启的共享

net share admin$ /delete  #删除admin共享                                                    

net share c$ /delete         #                                                

net share d$ /delete

net share c$=c: /yes

net share d$=c: /yes&lt; /FONT&gt;

net start #查看系统开启的服务

net start    servername        #启动服务

net user user1 /add #添加用户user1

net use \\ip\ipc$ &amp;apos;&amp;apos;password&amp;apos;&amp;apos; \user:&amp;apos;&amp;apos;username&amp;apos;&amp;apos;    #建立ipc连接

net use \\ip\ipc$   &amp;apos;&amp;apos;&quot; \user:&amp;apos;&amp;apos;&amp;apos;&amp;apos;  #建立ipc空连接(使用空的用户名密码)

net view     \\IP 查看远程主机共享资源