### Skill {#skill}

定制鼠标右键&quot;新建菜单&quot;选项

当您在Windows桌面单击鼠标右键，选择&quot;新建&quot;来建立快捷方式或文件夹时，除了快捷方式与文件夹这2个选项之外，还有一个很长的文件菜单，包含了电脑中安装的一些应用软件，您可以很容易地建立文件列表中所包含类型的新文件。我们在这里向您介绍如何通过修改注册表来定制鼠标右键快捷菜单中的 &quot;新建&quot;菜单所包含的项目。 需要注意的是，在修改注册表以前请先将注册表备份，以免出现问题时无法恢复。

一、增加菜单项目

1．首先，决定您要增加到菜单中的文件类型，以及启动这类文件的应用程序。如果是某些在启动时会自动打开的新文件或让您可以立即使用的应用程序，如记事本、写字板或画图等，就不需要特别的准备工作。但如果是在启动时不会自动打开文件的应用程序，您必须依需求建立一个通用的文件范本，并将它保存在 Windows中的ShellNew文件夹中。此文件夹在某些系统中是隐藏的，所以您可能必须先选择&quot;查看&quot;*&quot;文件夹选项&quot;，在&quot;查看&quot;选项卡中选取 &quot;显示所有文件&quot;选项，单击&quot;确定&quot;即可。

2．选择&quot;开始&quot;*&quot;运行&quot;，输入&quot;regedit&quot;，打开注册表编辑器。单击 &quot;HKEY_CLASSES_ROOT&quot;旁边的&quot;+&quot;号，可以看到左边窗口中有一排文件夹，都是以Windows中应用程序建立的文件的后缀名命名的 (如.doc、.xls和.html等)。找出您要增加到&quot;新建&quot;菜单中的文件类型的后缀名，单击鼠标右键，选择&quot;新建&quot;*&quot;主键&quot;(在注册表中，每个文件夹都是一个主键)，将新的主键取名为&quot;ShellNew&quot;。选取新建的主键，在右边视窗空白处单击鼠标右键，选择&quot;新增&quot;*&quot;字符串值&quot;。如果您使用的文件类型，其程序预设为在启动时打开空白文件，就将新字符串名称设定为&quot;NullFile&quot;; 如果您使用的文件类型，其程序在启动时不会自动打开空白文件的话，请将新字符串名称设定为&quot;FileName&quot;。双击&quot;FileName&quot;字符串图标(或选中后按Enter键)，在&quot;编辑字符串&quot;对话框的&quot;键值&quot;文本框中输入文件类型范本的完整路径及名称。然后按确定，退出注册表编辑器。您可以立刻在&quot;新建&quot;菜单的文件列表中看到所做的修改。

     以下是一个范例，要在桌面上或在文件夹中按右键建立新的Outlook Express 邮件。启动Outlook Express，选择&quot;文件&quot;*&quot;新建&quot;*&quot;邮件&quot;，再加入要放在邮件中的文字，然后选取&quot;文件&quot;*&quot;另存为&quot;，将邮件以&quot;blank&quot;的名称保存在\Windows\ShellNew文件夹中，Outlook Express 会自动为邮件加上.eml扩展名。接下来，依照前面的说明启动注册表编辑器，在HKEY_CLASSES_ROOT中找出.eml的文件夹，建立 &quot;ShellNew&quot;主键，在此主键中新建一个字符串值，并将其名称设定为&quot;FileName&quot;。双击&quot;FileName&quot;字符串，在&quot;编辑字符串&quot;对话框的&quot;键值&quot;文本框中输入&quot;C:\Windows\ShellNew\blank.eml&quot;(您可以自行设定路径和名称)。按下&quot;确定&quot;按钮，退出注册表编辑器即可。此时，您可以在桌面上按鼠标右键，选择&quot;新建&quot;*&quot;Outlook Express Mail Message&quot;(如附图所示)。桌面上就会出现一个新邮件图标，输入新邮件文件的名称并按下Enter键。双击新邮件的图标，输入邮件内容，完成之后，按下&quot;发送&quot;按钮即可。这一方法可用来建立电子邮件，并将邮件副本保存在Outlook Express(或其他类似的邮件程序)之外。

二、删除菜单项目

有许多种方法可以删除&quot;新建&quot;菜单中的文件类型列表，以下是3种方法。

1．删除您不使用的程序的文件类型，最好是卸载整个应用程序。可以利用&quot;控制面板&quot;中的&quot;添加/删除程序&quot;功能。此操作同时会将&quot;新建&quot;菜单的文件列表中的相应项目删除。2．如果您自行卸载软件后，该文件类型的菜单选项仍然存在，请进入资源管理器选择&quot;查看&quot;*&quot;文件夹选项&quot;，单击&quot;文件类型&quot;选项卡，选取您不再使用的文件类型，单击&quot;删除&quot;按钮，确认删除。如此可将文件类型从关联文件菜单、注册表以及&quot;新建&quot;菜单中删除。

3．如果您需要保留与文件类型相关的应用程序，只想删除&quot;新建&quot;菜单中的图标，请按前面说明打开注册表编辑器。单击 &quot;HKEY_CLASSES_ROOT&quot;前的&quot;+&quot;号，找出含有您要删除的文件类型的扩展名的文件夹，单击旁边的&quot;+&quot;号。在左边的树状图中，选取正确扩展名下的&quot;ShellNew&quot;文件夹。此时，您可以制作一个此注册表分支的备份，以便您恢复原有的设置(选择&quot;注册表&quot;*&quot;导出注册表文件&quot;，指定文件名称及保存的位置，&quot;导出范围&quot;项目中必须选中&quot;选择的分支&quot;，然后单击&quot;保存&quot;)。在右边窗口中选取&quot;NullFile&quot;或&quot;FileName&quot;，按下 Delete键，然后按Enter键。如果您希望将此项目恢复到功能表中，请找到您导出的.reg文件，双击将其恢复到注册表中。

修改系统默认安装位置

开始菜单-运行，输入regedit后确定打开注册表编辑器。展开HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion,然后在右窗中将C:\ProgramFilesDir改成x:\ProgramFiles,这样就把程序的安装位置从C盘改到了D盘。修改后须重启电脑才可生效。

OUTLOOK最小化到托盘

OUTLOOK启动后最小化总是在任务栏上占一个位置，工作起来碍事，所以希望它能够最小化到托盘，以下方法可以帮你实现：

1.打开注册表 : 开始菜单 -&gt; 运行, 输入&quot;regedit&quot;并回车

2.打开HKEY_CURRENT_USER\Software\Microsoft\Office\12.0\Outlook\Preferences项目

3.建立一个DWord的值(双字节值),名称为&quot;MinToTray&quot;, 取值改成 1

4.关闭注册表编辑器, 如果Outlook 2007运行中，关闭.

5.启动Outlook2007, 此时系统托盘区已经有一个Outlook2007的小图标了, 当你把Outlook2007最小化的时候, 它就会自己缩到托盘区了.