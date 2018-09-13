## w32tm {#w32tm}

[https://technet.microsoft.com/en-us/library/cc773263(WS.10).aspx](https://technet.microsoft.com/en-us/library/cc773263(WS.10).aspx)

[http://tilt.lib.tsinghua.edu.cn/node/882](http://tilt.lib.tsinghua.edu.cn/node/882)

服务器时间同步是一个容易被忽视的问题，但在企业级应用环境中，不同服务器之间的时间差很可能引发应用系统问题。Windows提供的w32tm程序可以用来设置时间同步服务器，其用法如下：

1、指定外部时间源并与之同步　　w32tm /config /manualpeerlist:&quot;210.72.145.44&quot; /syncfromflags:manual /reliable:yes /update　　/manualpeerlist表示外部时间源服务器列表，多个服务器之间可用空格分隔，210.72.145.44是中国国家授时中心的时间服务器ip地址　　/syncfromflags:manual表示与指定的外部时间源服务器列表中的服务器进行同步　　/reliable:yes设置此计算机是一个可靠的时间源。此设置只对域控制器有意义。　　/update向时间服务发出配置已更改的通知，使更改生效

2、显示本地时间与目的时间的时间差　　w32tm /stripchart /computer:210.72.145.44 /samples:30 /dataonly

3、显示目前服务器指定的外部时间源　　w32tm /query /source

4、恢复Windows Time Service的预设值　　net stop w32time　　w32tm /unregister　　w32tm /register　　net start w32time

　　在域环境中，只需设置根域控制器的外部时间源即可，其它服务器在添加进域中时将自动设置与域控制器时间同步。　　改设置可解决域控制器的时间同步问题 如：Time-Service EventID:36

更多用法详见w32tm的帮助吧

注: 以上时间服务器ip已经失效.

大家都知道计算机电脑的时间是由一块电池供电保持的，而且准确度比较差经常出现走时不准的时候。通过互联网络上发布的一些公用网络时间服务器NTP server，就可以实现自动、定期的同步本机标准时间。依靠windows系统默认的windows或NIST等境外的时间服务器同步时间，总存在着访问堵塞、时间延迟大（同步精度低）等因素的影响。现在中国的国家授时中心发布了一个时间服务器地址，大家可以用国人自己的标准时间！_方法一、采用系统自带的时间同步功能,以win7操作系统为例，单击系统托盘下方的时间，单击弹出窗口里的&quot;更改日期和时间设置&quot;，弹出&quot;日期和时间&quot;对话框，选择&quot;Internet时间&quot;选 项卡，单击&quot;更改设置&quot;按钮，弹出&quot;Internet时间设置&quot;对话框，在服务器地址栏输入国家授时中心服务器的IP地址：210.72.145.44， 单击&quot;立即更新&quot;按钮，同步完成后点击&quot;确定&quot;按钮退出，OK。方法二、修改注册表，提高时间同步精度由于系统默认的时间同步间隔是7天，我们无法自由选择，使得这个功能在灵活性方面大打折扣。其实，我们也可以通过修改注册表来手动修改它的自动同步间隔以提高同步精度，以下以Vista系统为例。1\. 在&quot;开始&quot;菜单→&quot;运行&quot;项下（或按Win+R）输入&quot;Regedit&quot;进入注册表编辑器。2\. 展开[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time \Parameters]分支，双击NtpServer将键值修改为国家授时中心服务器的IP地址：210.72.145.44，然后点击&quot;确定&quot;按钮保 存。（注：若已用过方法一，此步可以省略）3\. 展开[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time\1 lTimeProviders\NtpClient]分支，并双击SpecialPollInterval键值，将对话框中的&quot;基数栏&quot;选择到&quot;十进制&quot; 上，输入框中显示的数字正是自动对时的间隔(以秒为单位)，比如默认的604800就是由7(天)×24(时)×60(分)×60(秒)计算来的。设定时 间同步周期（建议设为900=15分钟或3600=1小时等周期值），填入对话框，点击确定保存关闭对话框。