#### nbtstat {#nbtstat}

NBTSTAT [ [-a RemoteName] [-A IP address] [-c] [-n]

       [-r] [-R] [-RR] [-s] [-S] [interval] ]

 -a   ( 适配器状态)    列出指定名称的远程机器的名称表

 -A   (适配器状态)    列出指定 IP 地址的远程机器的名称表。

 -c   (缓存)          列出远程[计算机]名称及其 IP 地址的 NBT 缓存

 -n   (名称)          列出本地 NetBIOS 名称。

 -r   (已解析)        列出通过广播和经由 WINS 解析的名称

 -R   (重新加载)      清除和重新加载远程缓存名称表

 -S   (会话)          列出具有目标 IP 地址的会话表

 -s   (会话)          列出将目标 IP 地址转换成计算机 NETBIOS 名称的会话表。

 -RR  (释放刷新)      将名称释放包发送到 WINS，然后启动刷新

 RemoteName   远程主机计算机名。

 IP address   用点分隔的十进制表示的 IP 地址。

 interval     重新显示选定的统计、每次显示之间暂停的间隔秒数。

              按 Ctrl+C 停止重新显示统计。