### GDR 和 QFE {#gdr-qfe}

微软已经为补丁中的更新系统文件划分了级别，其中 GDR 表示&quot;普通分发版本&quot;，而 QFE 则表示&quot;快速修补工程更新版本&quot;，其中 GDR 更新文件一般都进行了大量的严格测试，因此补丁的稳定性相对较高；而 QFE 更新文件一般所做的测试相对较少，因此其稳定性普遍不如 GDR。

由于更新文件划分了级别，因此 Windows 补丁也划分为两类：一类称为&quot;安全修补程序&quot;，这类补丁包同时包含 GDR 和 QFE 版本的更新文件，也就是两个副本，一般在 Windows 被发现严重漏洞时发布关键更新使用；第二类称为&quot;修复程序&quot;，一般都是一些非关键性更新，仅包含 QFE 版本的更新文件。

比如说我们现在要安装一个仅包含 QFE 版文件的非关键性更新。如果这个补丁需要更新的旧系统文件已经是 GDR 版，这时更新程序就会自动对比新旧文件的版本号。假如原先的 GDR 文件版本比补丁包中的 QFE 文件版本还要高，那么就会自动禁止补丁包中的 QFE 文件进行更新，而会改用和原 GDR    文件版本号相同的 QFE 版文件来更新。那么上哪里去找这个和原 GDR 文件版本号相同的 QFE 文件呢？实际这个文件已经在计算机硬盘里了，因为在上一次安装包含这个 GDR 文件的&quot;安全修补程序&quot;时，已经将同版本的 QFE 也复制到了系统中备用。这就是为什么&quot;安全修补程序&quot;要同时包含 GDR 和 QFE 两个副本的原因。

C:\Windows\System32\drivers\etc

HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.dll