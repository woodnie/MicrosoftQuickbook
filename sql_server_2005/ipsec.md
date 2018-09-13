### IPSEC {#ipsec}

[http://www.haogongju.net/art/708412](http://www.haogongju.net/art/708412)

本页内容

目标

适用范围

如何使用本章内容

摘要

您必须了解的背景知识

创建 IP 筛选器

创建筛选器操作

创建规则

将 IPSec 策略导出到远程计算机  

分配策略

验证它是否正常运行

其他资源

目标

本章的目标是：

? 使用 IPSec 在两台 Microsoft?

Windows? 2000 Server 计算机之间配置安全通道。

返回页首

适用范围

本章适用于以下产品和技术：

? Windows 2000 Server（带 Service Pack 3）

? Microsoft 网络监视器

? Microsoft .NET Framework 版本 1.0 (Service Pack 2) 以及更高版本

? Microsoft Visual Studio? 1.0 .NET 以及更高版本

? Microsoft Visual C#? .NET

? Microsoft SQL Server? 2000 (Service Pack 2) 以及更高版本

返回页首

如何使用本章内容

若要学好本章内容：

? 必须具有两台运行 Windows 2000 Server 操作系统的计算机，并配置如下：

? 固定 IP 地址。

? 数据库服务器计算机上具有 SQL Server 2000，且已安装了 Northwind 示例数据库。

? 您必须具有使用 Visual C# .NET 进行编程的经验。

? 您必须具有使用 Visual Studio .NET 开发环境的经验。

? 您必须具有使用 Windows 管理工具配置 Windows 2000 Server 的经验。

? 您必须具有使用网络监视器工具的经验。

? 阅读第 4 章安全通信。这一章概述了与通信通道相关的问题，并简要介绍了 IPSec。

返回页首

摘要

Internet 协议安全性 (IPSec) 是一种传输层机制，通过它可以确保在计算机之间传送的基于 TCP/IP 的通信的机密性和完整性。IPSec 还支持基于计算机的身份验证。由于具备这些特点，IPSec 已成为在计算机之间提供安全通信通道的理想之选，而且，它对于所有应用程序都是透明的。

本章介绍如何使用 IPSec 在两台计算机之间配置安全的通信通道。

返回页首

您必须了解的背景知识

Internet 协议安全性 (IPSec) 可用来保护在两台计算机（例如一台应用程序服务器与一台数据库服务器）之间传送的数据的安全。IPSec 对应用程序来说是完全透明的，因为加密、完整性和身份验证等服务是在传输层实现的。应用程序可以继续使用 TCP 端口和 UDP 端口以正常方式相互通信。

使用 IPSec，您可以：

? 对两台计算机之间传送的所有数据加密，从而实现消息机密性。

? 在两台计算机之间提供消息完整性（但不加密数据）。

? 在两台计算机之间相互验证身份。例如，您可以建立只允许特定客户端计算机（例如应用程序服务器或 Web 服务器）所发请求的策略，从而帮助保护数据库服务器的安全。

? 限制哪些计算机能够相互通信。您也可以限制只与特定的 IP 协议和 TCP/UDP 端口通信。

本章说明如何保护应用程序服务器与运行 SQL Server 2000 的数据库服务器之间的通信通道。应用程序服务器使用建议的 TCP/IP 客户端网络库连接到 SQL Server，并使用默认的 SQL Server TCP 端口 1433。图 1 中显示了此配置。

图 1

&quot;如何&quot;解决方案配置

本章说明如何使用一个简单的 IPSec 策略来实现以下功能：

? 应用程序服务器与 SQL Server 之间的通信只能通过端口 1433 使用 TCP 来实现。

? 丢弃所有其他 IP 数据包，包括 ICMP (ping)。

? 对在两台计算机之间传送的所有数据进行加密以保证机密性。

此方法的优点是：

? 可为在两台计算机之间传送的所有数据提供数据机密性。

? SQL Server 上的攻击面大大减少。剩下的唯一攻击点是以交互方式登录到数据库服务器，或者获得应用程序服务器的控制权并尝试在端口 1433 上通过 TCP 攻击 SQL Server。

? IPSec 策略的定义和实现非常简单。

此策略存在以下不足之处：

? SQL Server 不能与域控制器通信，因此：

? 无法应用组策略（数据库服务器应该是独立服务器）。

? 应用程序服务器与数据库服务器之间的 Windows 身份验证要求同步两台计算机上的本地帐户（具有相同的用户名和密码）。

? 不能使用更可靠的应用 IPSec 的方法（Windows 2000 默认方法/Kerberos）。

? SQL Server 不能与其他计算机（包括 DNS 服务器）通信。

? 本章介绍的方法使用预共享密钥身份验证，对于生产方案建议不要使用此方法。生产系统应该使用证书或 Windows 2000 域身份验证。使用预共享机密的 IPSec 策略只适合于开发或测试环境。

? 两台计算机都必须有静态 IP 地址。

备注

? IPSec 策略由一组筛选器、筛选器操作和规则组成。

? &quot;筛选器&quot;由以下内容组成：

? 源 IP 地址或地址范围。

? 目标 IP 地址或地址范围。

? IP 协议，如 TCP、UDP 或&quot;任意&quot;。

? 源端口和目标端口（仅限于 TCP 或 UDP）。

? 还可以在两台计算机上对筛选器进行镜像。镜像筛选器在客户端和服务器计算机上应用相同的规则（源地址和目标地址互换）。

? &quot;筛选器操作&quot;指定调用特定的筛选器时采取的操作。它可以是下面任何一种：

? 允许：通信不受保护；可以不受干预地进行发送和接收。

? 禁止：不允许通信。

? 协商安全性：终结点必须达成一致，然后使用安全方法进行通信。如果它们未就通信方法达成一致，则不会发生通信。如果协商失败，则可以指定是否允许不安全的通信或是否应禁止所有的通信。

? &quot;规则&quot;将筛选器与筛选器操作关联起来。

? &quot;镜像&quot;策略将规则应用于所有数据包（源 IP 地址和目标 IP 地址正好互换）。本章将创建镜像策略。

返回页首

创建 IP 筛选器

? 在数据库服务器计算机上创建新的 IP 筛选器

1.

作为管理员登录到数据库服务器。

2.

从&quot;管理工具&quot;程序组启动&quot;本地安全策略&quot;Microsoft 管理控制台 (MMC) 管理单元。

3.

在左窗格中，右键单击&quot;本地计算机上的 IP 安全策略&quot;，然后单击&quot;管理 IP 筛选器表和筛选器操作&quot;。

您将看到，此时已为所有 ICMP 通信和所有 IP 通信定义了两个筛选器列表。

4.

单击&quot;添加&quot;。

5.

在&quot;IP 筛选器列表&quot;对话框中，在&quot;名称&quot;字段中键入&quot;SQL Port&quot;。

6.

单击&quot;添加&quot;，然后单击&quot;下一步&quot;跳过&quot;IP 筛选器向导&quot;的欢迎对话框。

7.

在&quot;IP 通信源&quot;对话框中，从&quot;源地址&quot;下拉列表中选择&quot;一个特定的 IP 地址&quot;，然后输入您的应用程序服务器计算机的 IP 地址。

8.

单击&quot;下一步&quot;。

9.

在&quot;IP 通信目标&quot;对话框中，从&quot;目标地址&quot;下拉列表中选择&quot;一个特定的 IP 地址&quot;，然后输入您的数据库服务器计算机的 IP 地址。

10.

单击&quot;下一步&quot;。

11.

在&quot;IP 协议类型&quot;对话框中，选择&quot;TCP&quot;作为协议类型，然后单击&quot;下一步&quot;。

12.

在&quot;IP 协议端口&quot;对话框中，选择&quot;从任意端口&quot;，然后选择&quot;到此端口&quot;。输入&quot;1433&quot;作为端口号。

13.

单击&quot;下一步&quot;，然后单击&quot;完成&quot;关闭向导。

14.

单击&quot;关闭&quot;，关闭&quot;IP 筛选器列表&quot;对话框。

返回页首

创建筛选器操作

此过程创建两个筛选器操作。第一个用于禁止来自指定计算机的所有通信，第二个用于在应用程序服务器与数据库服务器计算机之间强制使用加密。

? 创建筛选器操作

1.

单击&quot;管理筛选器操作&quot;选项卡。

注意已经定义了几个预定义操作。

2.

单击&quot;添加&quot;创建新的筛选器操作。

在下面的步骤中，您将创建一个禁止操作，用以禁止来自所选计算机的所有通信。

3.

单击&quot;下一步&quot;跳过&quot;筛选器操作向导&quot;的初始对话框。

4.

在&quot;名称&quot;字段中，键入&quot;Block&quot;，然后单击&quot;下一步&quot;。

5.

在&quot;筛选器操作常规选项&quot;对话框中，选择&quot;禁止&quot;，然后单击&quot;下一步&quot;。

6.

单击&quot;完成&quot;关闭此向导。

7.

单击&quot;添加&quot;再次启动&quot;筛选器操作向导&quot;。

在下面的步骤中，您将创建一个筛选器操作，用以强制在应用程序服务器与数据库服务器计算机之间使用加密。

8.

单击&quot;下一步&quot;跳过&quot;筛选器操作向导&quot;的初始对话框。

9.

在&quot;名称&quot;字段中键入&quot;Require High Security&quot;，然后单击&quot;下一步&quot;。

10.

选择&quot;协商安全性&quot;，然后单击&quot;下一步&quot;。

11.

选择&quot;不与不支持 IPSec 的计算机通信&quot;，然后单击&quot;下一步&quot;。

12.

选择&quot;自定义&quot;，然后单击&quot;设置&quot;。

13.

确保选中&quot;数据完整性和加密 (ESP)&quot;复选框。

14.

从&quot;完整性算法&quot;下拉列表中选择&quot;SHA1&quot;。

15.

从&quot;加密算法&quot;下拉列表中选择&quot;3DES&quot;。

16.

选中&quot;会话密钥设置&quot;组中的两个复选框，分别每隔 100000 Kb 和每隔 3600 秒生成一个新的密钥。

17.

单击&quot;确定&quot;关闭&quot;自定义安全措施设置&quot;对话框，然后单击&quot;下一步&quot;。

18.

选中&quot;编辑属性&quot;复选框，然后单击&quot;完成&quot;。

19.

清除&quot;接受不安全的通讯，但总是用 IPSec 响应&quot;复选框。

20.

选中&quot;会话密钥完全向前保密&quot;复选框，然后单击&quot;确定&quot;。

21.

单击&quot;关闭&quot;以关闭&quot;管理 IP 筛选器表和筛选器操作&quot;对话框。

返回页首

创建规则

此过程创建两个新规则，用于将您在过程 1 中创建的筛选器与您在过程 2 中创建的两个筛选器操作关联起来。

? 创建规则

1.

在左窗格中，右键单击&quot;本地计算机上的 IP 安全策略&quot;，然后单击&quot;创建 IP 安全策略&quot;。

2.

单击&quot;下一步&quot;跳过&quot;IP 安全策略向导&quot;的初始对话框。

3.

在&quot;名称&quot;字段中，键入&quot;Secure SQL&quot;，然后单击&quot;下一步&quot;。

4.

清除&quot;激活默认响应规则&quot;复选框，然后单击&quot;下一步&quot;。

5.

选中&quot;编辑属性&quot;复选框，然后单击&quot;完成&quot;。

6.

单击&quot;添加&quot;启动&quot;安全规则向导&quot;。

7.

单击&quot;下一步&quot;跳过&quot;安全规则向导&quot;的初始对话框。

8.

单击&quot;此规则不指定隧道&quot;，然后单击&quot;下一步&quot;。

9.

单击&quot;所有网络连接&quot;，然后单击&quot;下一步&quot;。

10.

单击&quot;使用此字符串保护密钥交换（预共享密钥）&quot;。

11.

在文本框中输入&quot;MySecret&quot;作为&quot;机密&quot;密钥。

注意：两台计算机的此密钥必须相同才能成功通信。您应该使用长的随机数，但是在本章中使用&quot;MySecret&quot;就足够了。

12.

单击&quot;下一步&quot;。

13.

选择&quot;SQL Port&quot;选项。

注意：必须单击圆圈（单选按钮）而不是文本，才能选中该选项。

14.

单击&quot;下一步&quot;。

15.

选择&quot;需要高安全性&quot;选项，然后单击&quot;下一步&quot;。

16.

单击&quot;完成&quot;返回到&quot;Secure SQL 属性&quot;对话框。

17.

单击&quot;添加&quot;再次启动&quot;安全规则向导&quot;，然后单击&quot;下一步&quot;跳过初始对话框。

18.

单击&quot;此规则不指定隧道&quot;，然后单击&quot;下一步&quot;。

19.

单击&quot;所有网络连接&quot;，然后单击&quot;下一步&quot;。

20.

在&quot;身份验证方法&quot;对话框中，选中&quot;Windows 2000 默认值(Kerberos V5 协议)&quot;，然后单击&quot;下一步&quot;。

注意：此规则将指定&quot;Block&quot;（禁止）筛选器操作，因此不需要身份验证。

21.

在&quot;IP 筛选器列表&quot;对话框中，单击&quot;所有 IP 通信&quot;，然后单击&quot;下一步&quot;。

22.

在&quot;筛选器操作&quot;对话框中，选择&quot;Block&quot;（禁止）选项，然后单击&quot;下一步&quot;。

23.

单击&quot;完成&quot;。

24.

单击&quot;关闭&quot;以关闭&quot;Secure SQL 属性&quot;对话框。

返回页首

将 IPSec 策略导出到远程计算机

已经在数据库服务器上创建的 IPSec 策略现在必须导出并复制到应用程序服务器计算机中。

? 将 IPSec 策略导出到应用程序服务器计算机

1.

在左窗格中，右键单击&quot;本地计算机上的 IP 安全策略&quot;节点，指向&quot;所有任务&quot;，然后单击&quot;导出策略&quot;。

2.

在&quot;名称&quot;字段中，键入&quot;Secure SQL&quot;，然后单击&quot;保存&quot;将文件导出到本地硬盘上。

3.

将 .ipsec 文件直接复制到应用程序服务器上，或者使用文件共享使其可用。

重要说明：因为导出的策略文件包含明文形式的预共享密钥，所以必须适当地保护该文件。不要将其存储在任一台计算机的硬盘上。

4.

以管理员身份登录到应用程序服务器，并启动&quot;本地安全策略&quot;MMC 管理单元。

5.

选择并右键单击&quot;本地计算机上的 IP 安全策略&quot;，指向&quot;所有任务&quot;，然后单击&quot;导入策略&quot;。

6.

浏览到先前导出的 .ipsec 文件，单击&quot;打开&quot;以导入策略。

返回页首

分配策略

在 IPSec 策略变得活动之前，必须先分配该策略。注意，在一台特定的计算机上，任何时候只能有一个策略是活动的。

? 在应用程序服务器和数据库服务器计算机上分配 Secure SQL 策略

1.

在应用程序服务器计算机上，右键单击新导入的 Secure SQL 策略，然后单击&quot;分配&quot;。

2.

在数据库服务器计算机上重复上一步骤。

现在，在这两台计算机上都分配了镜像策略。

策略确保只有应用程序服务器可以和数据库服务器通信。此外，只允许使用端口 1433 的 TCP 连接，并且对两台计算机之间发送的所有通信都进行加密。

返回页首

验证它是否正常运行

此过程使用网络监视器来验证在应用程序服务器与数据库服务器之间发送的数据是否已加密。

? 验证它是否正常运行

1.

在应用程序服务器计算机上，使用 Visual Studio .NET 创建一个新的名为 SQLIPSecClient 的 C# 控制台应用程序。

2.

将下面的代码复制到 class1.cs，替换所有现有的代码。

注意：用数据库服务器的 IP 地址替换连接字符串中的 IP 地址。

using System;using System.Data;using System.Data.SqlClient;namespace SQLIPSecClient{  class Class1  {    [STAThread]    static void Main(string[] args)    {      // 使用您的数据库服务器的 IP 地址替换以下连接      // 字符串中的 IP 地址      SqlConnection conn = new SqlConnection(        &quot;server=192.168.12.11;database=NorthWind;Integrated Security=        &amp;apos;SSPI&amp;apos;&quot;);      SqlCommand cmd = new SqlCommand(                              &quot;SELECT ProductID, ProductName FROM                               产品&quot;);      try      {        conn.Open();        cmd.Connection = conn;        SqlDataReader reader = cmd.ExecuteReader();        while (reader.Read())        {          Console.WriteLine(&quot;{0} {1}&quot;,                      reader.GetInt32(0).ToString(),                      reader.GetString(1) );        }        reader.Close();      }      catch( Exception ex)      {      }      finally      {        conn.Close();      }    }  }}

3.

在&quot;生成&quot;菜单上，单击&quot;生成解决方案&quot;。

4.

为了使两台计算机之间的 Windows 身份验证取得成功，必须在数据库服务器计算机上复制当前以交互方式登录到应用程序计算机所用的帐户。确保用户名和密码都匹配。

您还必须使用 SQL Server 企业级管理器为新创建的帐户创建一个数据库登录，并在 Northwind 数据库中为此登录添加一个新的数据库用户。

5.

在两台计算机上暂时不指派 Secure SQL IPSec 策略：

1.

在应用程序服务器计算机上启动本地安全设置。

2.

单击&quot;本地计算机上的 IP 安全策略&quot;。

3.

在右窗格中，右键单击&quot;Secure SQL&quot;，然后单击&quot;不指派&quot;。

4.

在数据库服务器计算机上重复第 1 步到第 3 步。

6.

在数据库服务器计算机上，单击&quot;管理工具&quot;程序组中的&quot;网络监视器&quot;。

注意：Windows 2000 Server 提供网络监视器的限制版。Microsoft SMS 提供网络监视器的完全版。

如果您没有安装网络监视器，请转到控制面板中的&quot;添加或删除程序&quot;，单击&quot;添加/删除 Windows 组件&quot;，从&quot;Windows 组件&quot;列表中选择&quot;管理和监视工具&quot;，单击&quot;详细信息&quot;，然后单击&quot;网络监视工具&quot;。单击&quot;确定&quot;，然后单击&quot;下一步&quot;安装网络监视器的限制版。可能会提示您插入 Windows 2000 Server CD。

7.

在&quot;捕获&quot;菜单上，单击&quot;筛选器&quot;创建一个新的筛选器，配置它以查看在应用程序服务器与数据库服务器之间发送的 TCP/IP 网络通信。

8.

单击&quot;开始捕获&quot;按纽。

9.

返回到应用程序服务器计算机，然后运行测试控制台应用程序。Northwind 数据库的产品列表应显示在控制台窗口中。

10.

返回到数据库服务器，然后单击网络监视器中的&quot;停止并查看捕获&quot;按钮。

11.

双击第一个捕获的帧以查看捕获的数据。

12.

向下滚动以查看捕获的帧。您应该能看到明文形式的 SELECT 语句，后面带有从该数据库检索到的产品列表。

13.

在两台计算机上都分配 Secure SQL IPSec 策略：

1.

在应用程序服务器计算机上启动本地安全设置。

2.

单击&quot;本地计算机上的 IP 安全策略&quot;。

3.

在右窗格中，右键单击&quot;Secure SQL&quot;，然后单击&quot;分配&quot;。

4.

在数据库服务器计算机上重复步骤 a 到 c。

14.

在网络监视器中，关闭捕获窗口。

15.

单击&quot;开始捕获&quot;按钮，然后在&quot;保存文件&quot;消息框中单击&quot;否&quot;。

16.

返回到应用程序服务器计算机，再次运行测试控制台应用程序。

17.

返回到数据库服务器计算机，然后单击网络监视器中的&quot;停止并查看捕获&quot;。

18.

确认数据现在已变得难以看懂（因为已加密）。

19.

关闭网络监视器。

返回页首

其他资源

有关 IPSec 的更多信息，请参见 TechNet 上的&quot;IP Security and Filtering&quot;（IP 安全性和筛选）： [http://www.microsoft.com/technet/treeview/default.asp?url=/technet/prodtechnol/winxppro/reskit/prcc_tcp_erqb.asp?frame=true](http://www.microsoft.com/technet/treeview/default.asp?url=/technet/prodtechnol/winxppro/reskit/prcc_tcp_erqb.asp?frame=true) &gt;。

有关网络监视器的更多信息，请参见 MSDN 上的 Microsoft Platform SDK 的&quot;Network Monitor&quot;（网络监视器）部分： [http://msdn.microsoft.com/library/default.asp?url=/library/en-us/netmon/netmon/network_monitor.asp](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/netmon/netmon/network_monitor.asp) 。