## WMI {#wmi}

[https://msdn.microsoft.com/en-us/library/aa384642(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/aa384642(v=vs.85).aspx)

WMI是一系列能够用于日程管理工作的成熟技术，随着Windows远程管理时代的到来，因为可以在不重新配置防火墙允许DCOM流量，从而使得WMI变得更具吸引力。在所有与WMI相关的脚本工具中，PowerShell是学习、掌握和使用WMI最简单的一个。

学习WMI是一个漫长的过程，因为其中包含大量编程涉及的对象需要掌握，读者可以从微软脚本中心的脚本资料库[http://www.microsoft.com/technet/scriptcenter/](http://www.microsoft.com/technet/scriptcenter/) default.mspx中获取很多有用的知识。其中包含大量的脚本实例，绝大多数是使用WMI编程操作系统组件；另外一个获取WMI类参考的网址是[http://msdn.microsoft.com/en-us/library/aa394554.aspx](http://msdn.microsoft.com/en-us/library/aa394554.aspx)，这个页面是WMI类的资料索引。其中包含所有类完整的文档，可以从中间找到任何一个特定的属性和方法。最后，可以通过DMTF的规范[http://www.dmtf.org/standards/wbem](http://www.dmtf.org/standards/wbem)获取WBEM的整体概况并通过DMTF指南[http://www.wbemsolutions.com/tutorials/DMTF](http://www.wbemsolutions.com/tutorials/DMTF)获取标准的一些基本知识。

尽管WMI是个很复杂的主题，而且需要花很大精力才能熟练掌握，但是PowerShell提供了很好的支持并且能够很好地操作WMI对象。在本文采用WMI查询对象信息，WMI也支持订阅特定事件，在事件发生时将会收到通知。当前版本的PowerShell不支持订阅事件，为此需要安装一个管理单元，名为&quot;PSEventing&quot;

[https://msdn.microsoft.com/zh-cn/library/ms974579.aspx](https://msdn.microsoft.com/zh-cn/library/ms974579.aspx)

[http://itlab.idcquan.com/windows/special/Script/](http://itlab.idcquan.com/windows/special/Script/)