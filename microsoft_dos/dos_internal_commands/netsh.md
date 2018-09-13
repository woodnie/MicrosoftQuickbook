#### netsh {#netsh}

[http://technet.microsoft.com/zh-cn/library/cc779693%28v=ws.10%29.aspx](http://technet.microsoft.com/zh-cn/library/cc779693%28v=ws.10%29.aspx)

netsh -C interface dump&gt;d:\tengke.txt               # 导出网络配置

netsh -C interface dump&gt;d:\guangxinban.txt

netsh -f d:\tengke.txt             #导入网络配置

netsh -f d:\guangxinban.txt