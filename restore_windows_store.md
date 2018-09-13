## Restore Windows Store {#restore-windows-store}

Get-AppxPackage -allusers Microsoft.WindowsStore | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register &quot;$($_.InstallLocation)\AppXManifest.xml&quot;}

[https://www.winhelponline.com/blog/restore-windows-store-windows-10-uninstall-with-powershell/](https://www.winhelponline.com/blog/restore-windows-store-windows-10-uninstall-with-powershell/)