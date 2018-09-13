### Port list {#port-list}

epmap             135/tcp    loc-srv                #DCE endpoint resolution

epmap             135/udp    loc-srv                #DCE endpoint resolution

netbios-ns        137/tcp    nbname                 #NETBIOS Name Service

netbios-ns        137/udp    nbname                 #NETBIOS Name Service

netbios-dgm       138/udp    nbdatagram             #NETBIOS Datagram Service

netbios-ssn       139/tcp    nbsession              #NETBIOS Session Service

microsoft-ds      445/tcp

microsoft-ds      445/udp

135 端口的作用其实就是为RPC通信提供一种服务端口的映射功能。说简单一点，135端口就是RPC通信中的桥梁。

137端口的主要作用是在局域网中提供计算机的名字或IP地址查询服务，一般安装了NetBIOS协议后，该端口会自动处于开放状态。

138端口的主要作用就是提供NetBIOS环境下的计算机名浏览功能。

139端口是一种TCP端口，该端口在你通过网上邻居访问局域网中的共享文件或共享打印机时就能发挥作用。

445端口也是一种TCP端口，该端口在Windows 2000 Server或Windows Server 2003系统中发挥的作用与139端口是完全相同的。具体地说，它也是提供局域网中文件或打印机共享服务。不过该端口是基于CIFS协议（通用因特网文件系统协议）工作的，而139端口是基于SMB协议（服务器协议族）对外提供共享服务。同样地，攻击者与445端口建立请求连接，也能获得指定局域网内的各种共享信息。