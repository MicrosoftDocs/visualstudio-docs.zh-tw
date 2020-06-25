---
title: 設定 Windows 防火牆進行遠端偵錯 |Microsoft Docs
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350689"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>設定 Windows 防火牆以進行遠端偵錯程式

在受 Windows 防火牆保護的網路上，防火牆必須設定為允許遠端偵錯程式。 Visual Studio 和遠端偵錯程式會在安裝或啟動期間嘗試開啟正確的防火牆埠，但您可能也需要手動開啟埠或允許應用程式。

本主題說明如何設定 Windows 防火牆，以在 Windows 10、8/8.1 和7上啟用遠端偵錯。和 Windows Server 2012 R2、2012和 2008 R2 電腦。 Visual Studio 和遠端電腦不一定要執行相同的作業系統。 例如，Visual Studio 電腦可以執行 Windows 10，而遠端電腦則可以執行 Windows Server 2012 R2。

>[!NOTE]
>設定 Windows 防火牆的指示在不同作業系統和舊版 Windows 上稍有不同。 Windows 8/8.1、Windows 10 和 Windows Server 2012 設定使用 word*應用*程式，而 windows 7 和 windows server 2008 則使用 word*程式*。

## <a name="configure-ports-for-remote-debugging"></a>設定遠端偵錯程式的埠

Visual Studio 和遠端偵錯程式會在安裝或啟動期間嘗試開啟正確的埠。 不過，在某些情況下（例如協力廠商防火牆），您可能需要手動開啟埠。

**若要開啟埠：**

1. 在 Windows [**開始**] 功能表中，搜尋並開啟 [**具有 Advanced Security 的 Windows 防火牆**]。 在 Windows 10 中，這是**具有 Advanced Security 的 Windows Defender 防火牆**。

1. 針對新的傳入埠，選取 [**輸入規則**]，然後選取 [**新增規則**]。 針對傳出規則，請改為選取 [**輸出規則**]。

1. 在 [**新增輸入規則嚮導]** 中，選取 [**埠**]，然後選取 **[下一步]**。

1. 根據下表中的埠號碼，選取 [ **TCP** ] 或 [ **UDP**]。

1. 在 [**特定本機埠**] 底下，輸入下表中的埠號碼，然後選取 **[下一步]**。

1. 選取 **[允許連接**]，然後選取 **[下一步]**。

1. 選取一或多個要啟用的網路類型，包括遠端連線的網路類型，然後選取 **[下一步]**。

1. 新增規則的名稱（例如， **msvsmon**、 **IIS**或**Web Deploy**），然後選取 **[完成]**。

   [**輸入規則**] 或 [**輸出規則**] 清單中應該會出現並選取新的規則。

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>在遠端電腦上啟用遠端偵錯的連接埠

遠端偵錯程式必須在遠端電腦上開啟下列埠：

::: moniker range="vs-2017"

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|4022|傳入|TCP|針對 VS 2017。 每個 Visual Studio 版本的埠號碼遞增2。 如需詳細資訊，請參閱[Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|4023|傳入|TCP|針對 VS 2017。 每個 Visual Studio 版本的埠號碼遞增2。 此埠只會用來從遠端偵錯程式64位版本的32位進程進行遠端偵測。 如需詳細資訊，請參閱[Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|3702|傳出|UDP|選擇性遠端偵錯程式探索的必要。|

::: moniker-end

::: moniker range=">= vs-2019"

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|4024|傳入|TCP|針對 VS 2019。 每個 Visual Studio 版本的埠號碼遞增2。 如需詳細資訊，請參閱[Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|4025|傳入|TCP|針對 VS 2019。 每個 Visual Studio 版本的埠號碼遞增2。 此埠只會用來從遠端偵錯程式64位版本的32位進程進行遠端偵測。 如需詳細資訊，請參閱[Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)。|
|3702|傳出|UDP|選擇性遠端偵錯程式探索的必要。|

::: moniker-end

如果您選取 [**工具**] [選項] 下的 [**使用受控相容性模式]**  >  **Options**  >  ** **，請開啟這些額外的遠端偵錯程式埠 偵錯工具管理的相容性模式可讓舊版的 Visual Studio 2010 版的偵錯工具。

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|135、139、445|傳出|TCP|必要。|
|137、138|傳出|UDP|必要。|

如果您的網域原則需要透過 IPSec 執行網路通訊，您必須同時在 Visual Studio 和遠端電腦上開啟其他埠。 若要在遠端 IIS web 伺服器上進行調試，請開啟遠端電腦上的埠80。

|**連接埠**|**傳入/傳出**|**通訊協定**|**說明**|
|-|-|-|-|
|500、4500|傳出|UDP|如果您的網域原則需要透過 IPSec 進行網路通訊時，則為必要項。|
|80|傳出|TCP|網頁伺服器偵錯的必要項。|

若要允許特定的應用程式通過 Windows 防火牆，請參閱[設定 Windows 防火牆的遠端偵錯](#configure-remote-debugging-through-windows-firewall)程式。

## <a name="configure-remote-debugging-through-windows-firewall"></a>透過 Windows 防火牆設定遠端偵錯

您可以在遠端電腦上安裝遠端偵錯程式，或從共用資料夾執行這些工具。 不論是哪一種情況，都必須正確設定遠端電腦防火牆。

在遠端電腦上，遠端偵錯工具位於：

*\<Visual Studio installation directory\>\\Common7 \\ IDE \\ 遠端偵錯程式\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>允許和設定透過 Windows 防火牆的遠端偵錯程式

1. 在 Windows [**開始**] 功能表中，搜尋並開啟 [ **windows 防火牆**] 或 [ **windows Defender 防火牆**]。

1. 選取 [**允許應用程式通過 Windows 防火牆**]。

1. 如果 [**允許的應用程式和功能**] 底下未顯示**遠端偵錯程式**或**Visual Studio 遠端偵錯工具**，請選取 [**變更設定**]，然後選取 [**允許另一個應用程式**]。

1. 如果 [**新增應用**程式] 對話方塊中仍未列出遠端偵錯程式應用程式，請選取 **[流覽]**，然後 \<Visual Studio installation directory\> \\ \\ \\ \\ \<x86*, *x64*, or *Appx*\> 根據您應用程式的適當架構，流覽至 * Common7 IDE 遠端偵錯程式。 選取 [ *msvsmon.exe*]，然後選取 [**新增**]。

1. 在 [**應用程式**] 清單中，選取您剛才新增的**遠端偵錯程式**。 選取 [**網路類型**]，然後選取一或多個網路類型，包括遠端連線的網路類型。

1. 選取 [新增]****，然後選取 [確定]****。

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>針對遠端偵錯連結進行疑難排解

如果您無法使用遠端偵錯程式附加至應用程式，請確定遠端偵錯程式防火牆埠、通訊協定、網路類型和應用程式設定都正確無誤。

- 在 Windows [**開始**] 功能表中，搜尋並開啟 [ **windows 防火牆**]，然後選取 [**允許應用程式通過 Windows 防火牆**]。 請確定**遠端偵錯程式**或**Visual Studio 遠端偵錯工具**出現在 [**允許的應用程式和功能**] 清單中，並選取核取方塊，並選取正確的網路類型。 如果不是，請[新增正確的應用程式和設定](#configure-remote-debugging-through-windows-firewall)。

- 在 Windows [**開始**] 功能表中，搜尋並開啟 [**具有 Advanced Security 的 Windows 防火牆**]。 請確定 [**輸入規則**] 下的 [**遠端偵錯程式**] 或 [ **Visual Studio 遠端偵錯工具**] （選擇性的**輸出規則**）會出現綠色核取記號圖示，而且所有設定都是正確的。

  - 若要查看或變更規則設定，請以滑鼠右鍵按一下清單中的 [**遠端偵錯**程式] 應用程式，然後選取 [**屬性**]。 使用 [**屬性**] 索引標籤來啟用或停用規則，或變更埠號碼、通訊協定或網路類型。
  - 如果 [規則] 清單中未顯示遠端偵錯程式應用程式，請[新增並設定正確的埠](#configure-ports-for-remote-debugging)。

## <a name="see-also"></a>另請參閱

- [遠端偵錯](../debugger/remote-debugging.md)
- [Visual Studio 遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)
