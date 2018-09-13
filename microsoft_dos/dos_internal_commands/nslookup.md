#### nslookup {#nslookup}

C:\Users\Administrator&gt;nslookup

默认服务器:  ns-px.online.sh.cn

Address:  202.96.209.5

&gt; set type=A       #查询A记录

&gt; www.baidu.com

服务器:  ns-px.online.sh.cn

Address:  202.96.209.5

非权威应答:

名称:     www.a.shifen.com

Addresses:  119.75.218.45

                  119.75.217.56

Aliases:   www.baidu.com

&gt; set type=PTR        #查询PTR记录

&gt;  119.75.218.45

服务器:  ns-px.online.sh.cn

Address:  202.96.209.5

*** ns-px.online.sh.cn 找不到 45.218.75.119.in-addr.arpa.: Non-existent domain

&gt; 119.75.217.56

服务器:  ns-px.online.sh.cn

Address:  202.96.209.5

*** ns-px.online.sh.cn 找不到 56.217.75.119.in-addr.arpa.: Non-existent domain

&gt;