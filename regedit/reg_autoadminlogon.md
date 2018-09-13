### Reg AutoAdminLogon {#reg-autoadminlogon}

自动完成登录操作：

1、在运行对话框中，输入注册表编辑命令regedit，来打开注册表编辑窗口；

2、在该窗口中，依次展开HKEY_LOCAL_MACHINES\SOFTWARE\Microsoft\WindowsNT\Current Version\WinLogon键值；

3、在对应右边的子窗口中，用鼠标右键单击空白处，从弹出的快捷菜单中，依次执行&quot;新建&quot;/&quot;字符串&quot;命令，来创建一个字符串类型的键名，并将键名设置为&quot;AutoAdminLogon&quot;，并将该键名的数值设置为&quot;1&quot;；

4、找到&quot;DefaultDomainName&quot;键名，并用鼠标双击之，在随后出现的窗口中，输入要登录的域名，例如Department；

5、双击&quot;DefaultUserName&quot;键名，在随后打开的窗口中，直接输入要登录到此域的用户名，例如&quot;test&quot;；

6、在WinLogon右边的子窗口中，用鼠标右键单击空白处，从弹出的快捷菜单中，依次执行&quot;新建&quot;/&quot;字符串&quot;命令，来创建一个字符串类型的键名，并将键名设置为&quot;DefaultPassword&quot;，并将该键名的数值设置为用户登录系统的密码，例如用户test的登录密码为&quot;123456&quot;；

7、完成设置后，重新启动计算机时，我们会发现不需要再登录，就能自动进入到Windows Server 2000系统中了。以后要取消自动登录功能的话，可以将&quot;AutoAdminLogon&quot;键值设置为&quot;0&quot;就可以了。

Windows Registry Editor Version 5.00

[HKEY_LCOAL_MACHINE\Software\Microsoft\windows NT\currentversion\winlogo]

&quot;AutoAdminLogon&quot;=&quot;1&quot;

&quot;DefaultPassWord&quot;=&quot;你登录的密码&quot;

&quot;DefaultUserName&quot;=&quot;输入你登录的用户名&quot;

&quot;DefaultDomainName&quot;=&quot;微机名称&quot;