### ChangeKey {#changekey}

簡介

警告 本文中的步驟只有在「大量授權」媒體上才能生效。如果您嘗試在 OEM 媒體或零售版媒...

其他相關資訊

先決條件

在開始使用本文的資訊前，您必須擁有一個有效的產品金鑰。若要取得一個有效的產品金鑰，請按一下下列連結，連絡 Microsoft 大量授權服務中心：

[https://www.microsoft.com/licensing/servicecenter/home.aspx](https://www.microsoft.com/licensing/servicecenter/home.aspx)

回此頁最上方

變更大量授權產品金鑰的步驟

本文說明在「大量授權」安裝之後，變更 Windows XP 產品金鑰的兩種問題解決方法。一種方法是使用「Windows 啟用精靈」圖形化使用者介面 (GUI)，另一種方法則是使用 Windows Management Instrumentation (WMI) 指令碼。「啟用精靈」這個方法比較容易，但是，如果您必須變更多部電腦的產品金鑰，使用指令碼方法比較適當。

方法 1：使用「啟用精靈」

重要 這個章節、方法或工作包含的步驟會告訴您要如何修改登錄。然而，如果登錄修改錯誤，可能會發生嚴重的問題。因此，請確定小心執行下列步驟。為加強保護，修改登錄之前，請務必將它備份起來。如果發生問題，您就可以還原登錄。如需有關如何備份和還原登錄的詳細資訊，請按一下下面的文件編號，檢視「Microsoft 知識庫」中的文件：

322756  如何在 Windows XP 和 Windows Server 2003 中備份、編輯及還原登錄

如果您要進行變更的大量授權產品金鑰只有少數幾個，則可以使用「啟用精靈」。

注意 我們建議您在依照下列步驟執行之前，先執行「系統還原」以建立新的還原點。

停用 Windows

   按一下 [開始]，然後按一下 [執行]。

   在 [開啟] 方塊中，輸入 regedit，然後按一下 [確定]。

   在功能窗格中，找出並按一下下列登錄機碼：

   HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\Current Version\WPAEvents

   在主題窗格中，用滑鼠右鍵按一下 [OOBETimer]，然後按一下 [修改]。

   至少變更這個數值的其中一個數字，來停用 Windows。

重新啟用 Windows 並新增新的產品金鑰

   按一下 [開始]，然後按一下 [執行]。

   在 [開啟] 方塊中，輸入下列命令，然後按一下 [確定]。

   %systemroot%\system32\oobe\msoobe.exe /a

   按一下 [是，我想要打電話給客戶服務代表來啟用 Windows]，然後按一下 [下一步]。

   按一下 [變更產品金鑰]。

   在 [新金鑰] 方塊中輸入新的產品金鑰，然後按一下 [更新]。

   如果您返回到前一個視窗，按一下 [以後提醒我]，然後重新啟動電腦。

   重複執行步驟 1 和 2，以確認是否已啟用 Windows。您會收到下列訊息：

   Windows 已經啟用。請按 [確定] 結束。

   按一下 [確定]。

   安裝 Windows XP Service Pack 1a 或較新版的 Windows XP。

如果您在安裝 Windows XP SP1 或較新版的 Windows XP 之後，無法重新啟動 Windows，請嘗試下列步驟：

   重新啟動電腦，並開始按下 F8 直到您看見 [Windows 進階選項] 功能表。

   在功能表中選取 [上次的良好設定]，然後按下 ENTER。此選項會使用先前良好的設定來啟動 Windows。

   重複「重新啟用 Windows 並新增新的產品金鑰」中的步驟 1 到步驟 8。

如果您可以安裝 SP1 或較新版的 Windows XP，而且可以啟動 Windows，表示問題已解決。如果問題尚未解決，請嘗試方法 2 或參閱＜下一個步驟＞一節，以取得更多疑難排解資源。

方法 2：使用指令碼

如果您必須變更多部電腦的產品金鑰，我們建議您使用此方法。您可以建立變更大量授權產品金鑰的 WMI 指令碼，然後再將此指令碼部署到啟動指令碼中。

此節所說明的範例 ChangeVLKey2600.vbs 指令碼和範例 ChangeVLKeySP1 指令碼，會使用您要輸入的新大量授權金鑰做為單一引數。單一引數由五部分的英數字元格式構成。

我們建議您在 Windows XP 電腦上，針對非 Windows XP SP1 和較新版 Windows XP 使用 ChangeVLKey2600.vbs 指令碼，而針對 Windows XP SP1 和較新版 Windows XP 使用 ChangeVLKeySP1.vbs 指令碼。這些指令碼會執行下列功能：

   會移除五部分英數字元產品金鑰的連字號字元 (-)。

   會建立 win32_WindowsProductActivation 類別的例項。

   會以新的大量授權產品金鑰呼叫 SetProductKey 方法。

您可以建立批次檔或 cmd 檔案，此檔案會將下列其中一個範例指令碼搭配新的產品金鑰，作為引數；或是將其部署為啟動指令碼的一部分，或是從命令列加以執行來變更單一電腦上的產品金鑰。

範例

如需有關如何撰寫產品金鑰指令碼的詳細資訊，請造訪下列 Microsoft 網站：

[http://technet.microsoft.com/zh-tw/library/bb457096.aspx](http://technet.microsoft.com/zh-tw/library/bb457096.aspx)

ChangeVLKeySP1.vbs

&amp;apos;

&amp;apos; WMI 指令碼 - ChangeVLKey.vbs

&amp;apos;

&amp;apos; 此指令碼會變更電腦上的產品金鑰

&amp;apos;

&amp;apos;***************************************************************************

ON ERROR RESUME NEXT

if Wscript.arguments.count&lt;1 then

Wscript.echo &quot;指令碼必須有 VolumeProductKey 引數才能執行&quot;

Wscript.echo &quot;正確用法：Cscript ChangeVLKey.vbs ABCDE-FGHIJ-KLMNO-PRSTU-WYQZX&quot;

Wscript.quit

end if

Dim VOL_PROD_KEY

VOL_PROD_KEY = Wscript.arguments.Item(0)

VOL_PROD_KEY = Replace(VOL_PROD_KEY,&quot;-&quot;,&quot;&quot;) &amp;apos;移除連字號 (如果有的話)

for each Obj in GetObject(&quot;winmgmts:{impersonationLevel=impersonate}&quot;).InstancesOf (&quot;win32_WindowsProductActivation&quot;)

result = Obj.SetProductKey (VOL_PROD_KEY)

if err &lt;&gt; 0 then

WScript.Echo Err.Description, &quot;0x&quot; &amp; Hex(Err.Number)

Err.Clear

end if

Next

ChangeVLKey2600.vbs

&amp;apos;

&amp;apos; WMI 指令碼 - ChangeVLKey.vbs

&amp;apos;

&amp;apos; 此指令碼會變更電腦上的產品金鑰

&amp;apos;

&amp;apos;***************************************************************************

ON ERROR RESUME NEXT

if Wscript.arguments.count&lt;1 then

Wscript.echo &quot;指令碼必須有 VolumeProductKey 引數才能執行&quot;

Wscript.echo &quot;正確用法：Cscript ChangeVLKey.vbs ABCDE-FGHIJ-KLMNO-PRSTU-WYQZX&quot;

Wscript.quit

end if

Dim VOL_PROD_KEY

VOL_PROD_KEY = Wscript.arguments.Item(0)

VOL_PROD_KEY = Replace(VOL_PROD_KEY,&quot;-&quot;,&quot;&quot;) &amp;apos;移除連字號 (如果有的話)

Dim WshShell

Set WshShell = WScript.CreateObject(&quot;WScript.Shell&quot;)

WshShell.RegDelete &quot;HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WPAEvents\OOBETimer&quot; &amp;apos;刪除 OOBETimer 登錄值

for each Obj in GetObject(&quot;winmgmts:{impersonationLevel=impersonate}&quot;).InstancesOf (&quot;win32_WindowsProductActivation&quot;)

result = Obj.SetProductKey (VOL_PROD_KEY)

if err &lt;&gt; 0 then

WScript.Echo Err.Description, &quot;0x&quot; &amp; Hex(Err.Number)

Err.Clear

end if

下一頁

下列範例顯示如何從命令列使用 ChangeVLKeySP1.vbs 指令碼：

   按一下 [開始]，然後按一下 [執行]。

   在 [開啟] 方塊中，輸入下列命令，其中 AB123-123AB-AB123-123AB-AB123 是您要使用的新產品金鑰，然後按一下 [確定]：

   c:\changevlkeysp1.vbs ab123-123ab-ab123-123ab-ab123

如需有關正版 Microsoft 軟體的詳細資訊，請造訪下列 Microsoft 網站：

[http://www.microsoft.com/genuine/default.aspx](http://www.microsoft.com/genuine/default.aspx)

如果您可以安裝 SP1 或較新版的 Windows XP，而且您可以啟動 Windows，表示問題已解決。如果問題尚未解決，請參閱＜下一個步驟＞一節。

回此頁最上方