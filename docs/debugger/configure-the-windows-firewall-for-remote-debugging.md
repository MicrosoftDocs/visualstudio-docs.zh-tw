---
title: 設定 Windows 防火牆進行遠端偵錯 |Microsoft 檔
description: 設定 Windows 防火牆進行遠端偵錯。 設定遠端偵錯程式的埠。 疑難排解遠端偵錯連接。
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 52264580e428fa6a2c33d80ea8fb9fb8e07f0c59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149323"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>設定 Windows 防火牆以進行遠端偵錯

在受 Windows 防火牆保護的網路上，必須將防火牆設定為允許遠端偵錯程式。 Visual Studio 和遠端偵錯程式會嘗試在安裝或啟動期間開啟正確的防火牆埠，但您可能也需要手動開啟埠或允許應用程式。

本主題說明如何設定 Windows 防火牆，以便在 Windows 10、8/8.1 和7上啟用遠端偵錯。以及 Windows Server 2012 R2、2012和 2008 R2 電腦。 Visual Studio 和遠端電腦不需要執行相同的作業系統。 例如，Visual Studio 電腦可以執行 Windows 10，而遠端電腦則可以執行 Windows Server 2012 R2。

>[!NOTE]
>針對不同的作業系統和舊版 Windows，設定 Windows 防火牆的指示稍有不同。 Windows 8/8.1、Windows 10 和 Windows Server 2012 設定會使用 word *應用* 程式，而 windows 7 和 windows server 2008 則使用 word *程式*。

## <a name="configure-ports-for-remote-debugging"></a>設定遠端偵錯程式的埠

Visual Studio 和遠端偵錯程式會嘗試在安裝或啟動期間開啟正確的埠。 不過，在某些情況下，例如協力廠商防火牆，您可能需要手動開啟埠。

**若要開啟埠：**

1. 在 Windows [ **開始** ] 功能表中，搜尋並開啟 [ **具有 Advanced Security 的 Windows 防火牆**]。 在 Windows 10 中，這是 **具有 Advanced Security 的 Windows Defender 防火牆**。

1. 針對新的連入埠，選取 [ **輸入規則** ]，然後選取 [ **新增規則**]。 若為外寄規則，請改為選取 **輸出規則** 。

1. 在 [ **新增輸入規則] 嚮導** 中，選取 [ **埠**]，然後選取 **[下一步]**。

1. 根據下表中的埠號碼，選取 [ **TCP** ] 或 [ **UDP**]。

1. 在 [ **特定本機埠**] 下，輸入下清單格中的埠號碼，然後選取 **[下一步]**。

1. 選取 **[允許連接**]，然後選取 **[下一步]**。

1. 選取要啟用的一或多個網路類型，包括遠端連線的網路類型，然後選取 **[下一步]**。

1. 新增規則的名稱 (例如， **msvsmon**、 **IIS** 或 **Web Deploy**) ，然後選取 **[完成]**。

   新的規則應該會出現，並在 [ **輸入規則** ] 或 [ **輸出規則** ] 清單中選取。

**使用 PowerShell 開啟埠：**

針對 Windows 防火牆，您可以使用 PowerShell 命令，例如 [>new-netfirewallrule](/powershell/module/netsecurity/new-netfirewallrule?view=win10-ps)。

下列範例會在遠端電腦上開啟遠端偵錯程式的埠4024。 您需要使用的路徑可能不同。

```ps
New-NetFirewallRule -DisplayName "msvsmon" -Direction Inbound -Program "Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe" -LocalPort 4024 -Protocol TCP -Authentication Required -Action Allow
```

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>在遠端電腦上啟用遠端偵錯的連接埠

遠端偵錯程式必須在遠端電腦上開啟下列埠：

::: moniker range="vs-2017"

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|4022|正在傳入|TCP|針對 VS 2017。 每個 Visual Studio 版本的埠號碼會遞增2。 如需詳細資訊，請參閱 [Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|4023|正在傳入|TCP|針對 VS 2017。 每個 Visual Studio 版本的埠號碼會遞增2。 此埠僅用來從遠端偵錯程式的64位版本進行遠端偵錯程式的32位處理常式。 如需詳細資訊，請參閱  [Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|3702|傳出|UDP| (遠端偵錯程式探索所需的選擇性) 。|

::: moniker-end

::: moniker range=">= vs-2019"

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|4024|正在傳入|TCP|針對 VS 2019。 每個 Visual Studio 版本的埠號碼會遞增2。 如需詳細資訊，請參閱 [Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|4025|正在傳入|TCP|針對 VS 2019。 每個 Visual Studio 版本的埠號碼會遞增2。 此埠僅用來從遠端偵錯程式的64位版本進行遠端偵錯程式的32位處理常式。 如需詳細資訊，請參閱  [Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|3702|傳出|UDP| (遠端偵錯程式探索所需的選擇性) 。|

::: moniker-end

如果您選取 [**工具** 選項偵錯工具] 下的 [**使用 Managed 相容性模式]**  >    >  ****，請開啟這些額外的遠端偵錯程式埠 偵錯工具管理的相容性模式會啟用舊版的 Visual Studio 2010 版本的偵錯工具。

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|135、139、445|傳出|TCP|必要。|
|137、138|傳出|UDP|必要。|

如果您的網域原則需要透過 IPSec 執行網路通訊，您必須在 Visual Studio 和遠端電腦上開啟其他埠。 若要在遠端 IIS web 伺服器上進行調試，請在遠端電腦上開啟埠80。

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|500、4500|傳出|UDP|如果您的網域原則需要透過 IPSec 進行網路通訊時，則為必要項。|
|80|傳出|TCP|網頁伺服器偵錯的必要項。|

若要允許特定應用程式通過 Windows 防火牆，請參閱 [設定透過 Windows 防火牆進行遠端偵錯](#configure-remote-debugging-through-windows-firewall)。

## <a name="configure-remote-debugging-through-windows-firewall"></a>設定透過 Windows 防火牆進行遠端偵錯

您可以在遠端電腦上安裝遠端偵錯程式，或從共用資料夾執行這些工具。 無論是哪一種情況，都必須正確設定遠端電腦防火牆。

在遠端電腦上，遠端偵錯工具位於：

*\<Visual Studio installation directory\>\\Common7 \\ IDE \\ 遠端偵錯程式\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>透過 Windows 防火牆允許和設定遠端偵錯程式

1. 在 Windows [ **開始** ] 功能表中，搜尋並開啟 [ **windows 防火牆**] 或 [ **windows Defender 防火牆**]。

1. 選取 [ **允許應用程式通過 Windows 防火牆**]。

1. 如果 [**允許的應用程式和功能**] 下的 **[遠端偵錯程式**] 或 **[Visual Studio 遠端偵錯程式**] 未出現，請選取 [**變更設定**]，然後選取 [**允許**

1. 如果遠端偵錯程式應用程式仍未列在 [**新增應用程式**] 對話方塊中，請選取 **[流覽]**，然後 \<Visual Studio installation directory\> \\ \\ \\ \\ \<x86*, *x64*, or *Appx*\> 根據您應用程式的適當架構，流覽至 * Common7 IDE 遠端偵錯程式。 選取 *msvsmon.exe*，然後選取 [ **新增**]。

1. 在 [ **應用程式** ] 清單中，選取您剛剛新增的 **遠端偵錯程式** 。 選取 [ **網路類型**]，然後選取一或多個網路類型，包括遠端連線的網路類型。

1. 選取 [新增]，然後選取 [確定]。

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>疑難排解遠端偵錯連接

如果您無法使用遠端偵錯程式附加至您的應用程式，請確定遠端偵錯程式防火牆埠、通訊協定、網路類型和應用程式設定都正確無誤。

- 在 Windows [ **開始** ] 功能表中，搜尋並開啟 [ **windows 防火牆**]，然後選取 [ **允許應用程式通過 Windows 防火牆**]。 確定 [ **遠端偵錯程式** ] 或 [ **Visual Studio 遠端偵錯程式** ] 會出現在 [ **允許的應用程式和功能** ] 清單中，並選取核取方塊，並選取正確的網路類型。 如果沒有，請 [新增正確的應用程式和設定](#configure-remote-debugging-through-windows-firewall)。

- 在 Windows [ **開始** ] 功能表中，搜尋並開啟 [ **具有 Advanced Security 的 Windows 防火牆**]。 請確定 [**輸入規則**] 下出現 [**遠端偵錯程式**] 或 [ **Visual Studio 遠端偵錯程式**] (以及選擇性地) 具有綠色核取記號圖示的 **輸出規則**，而且所有設定都是正確的。

  - 若要查看或變更規則設定，請在清單中的 **遠端偵錯** 程式應用程式上按一下滑鼠右鍵，然後選取 [ **屬性**]。 您可以使用 [ **屬性** ] 索引標籤來啟用或停用規則，或變更埠號碼、通訊協定或網路類型。
  - 如果「遠端偵錯程式」應用程式未出現在 [規則] 清單中，請 [新增並設定正確的埠](#configure-ports-for-remote-debugging)。

## <a name="see-also"></a>另請參閱

- [遠端偵錯](../debugger/remote-debugging.md)
- [Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)
