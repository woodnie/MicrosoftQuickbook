### add app to mouse right {#add-app-to-mouse-right}

在鼠标右键添加程序

当在一个文件上右击时，弹的快捷菜单是否没有你想要的程序呢？别急，下面的方法会帮你搞定的：）

   打开注册表，定位到HKEY_CLASSES_ROOT\*下，在下面新建项shell,在新建的shell下再新建项，这个项是由你自己来定义的，也是出现在右键快捷菜单里的名称，因为我要把notepad++添加到鼠标右键，所以在这里我起的名字叫notepad++.

   在notepad++下面再建立新项command，然后修改项里的值，把值改为你要添加的程序的路径，然后加%1（这个要是打开的文件名的参数），我写的是这样的D:\ansi\notepad++ %1

   ok。

   截图如下