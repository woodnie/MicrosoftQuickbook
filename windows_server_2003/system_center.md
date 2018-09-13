### System Center {#system-center}

System Center 是微软著名的管理平台软件，在实现Microsoft的MOF&amp;ITIL的IT管理理念的过程中发挥了很重要的作用，System Center可以在MOF的每一个运维象限中都有对应的System Center产品协助企业实现动态的IT管理。System Center可以帮助企业的IT人员构建易于管理的系统并进行自动化操作，从而降低了成本、提高了应用系统的可用性、并改进了所提供的服务。

System Center Configuration Manager

System Center Configuration Manager（简称SCCM）的前身就是大家耳熟能详的System Managementr Server，这是一款非常优秀的桌面管理软件，可以极大地提高运维工程师的管理效率。看看SCCM提供的功能吧，它可以收集硬件和软件清单，在客户机上发布软件；它可以管理客户机更新，甚至可以拒绝没有及时更新修补程序的客户机访问网络；它还可以在裸机上部属操作系统；远程控制客户机；统计软件的使用次数….从这些功能中不难发现，SCCM确实是为优化桌面系统管理而设计的！

        本次系列中我们将为大家介绍最新版本的SCCM 2007 R2的部属，管理及常见应用。具体内容如下所示：

一 SCCM2007 R2的部署前准备

二 SCCM2007 R2安装详解

三 SCCM2007 R2的主站点配置及客户端安装

四 SCCM2007 R2实现资产管理

五 SCCM2007 R2分发软件

六 SCCM2007 R2管理Windows更新

七 SCCM2007实现软件计数

八 SCCM2007 OSD部属Win7

(微软为企业用户提供了WSUS（Windows Server Update Services）作为解决方案。WSUS解决问题的思路很简单，管理员利用WSUS服务器从微软的更新网站下载补丁，然后再发布给内网用)

Data Protection Manager

DPM是微软大名鼎鼎的System Center家族中的重要成员，它的拿手好戏就是对企业内的数据进行全方位的保护。DPM可以对企业内的诸多微软产品进行备份和还原，DPM不仅能支持文件服务器，Exchange，SQL Server，Sharepoint等常见的服务器应用，还可以支持XP等客户机系统。最难得的是，DPM不仅能提供可靠且不间断的数据保护服务，操作界面还非常友好，即使是第一次接触，DPM也非常容易上手。