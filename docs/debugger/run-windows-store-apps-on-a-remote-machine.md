---
title: 在遠端電腦上的 UWP 應用程式進行偵錯 |Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 8fec6295fce7f100b0dc8c602a41f95e1af7d64f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892247"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>從 Visual Studio 的遠端電腦上的 UWP 應用程式進行偵錯
  
您可以使用 Visual Studio 來執行、 偵錯、 剖析及測試在另一部電腦或裝置上的通用 Windows 平台 (UWP) 應用程式。 在遠端電腦上執行 UWP 應用程式時特別有幫助 Visual Studio 電腦不支援 UWP 特有的功能，例如觸控、 地理位置或實體的方向。 

##  <a name="BKMK_Prerequisites"></a> 必要條件  

若要偵錯在遠端裝置上從 Visual Studio 的 UWP 應用程式：  
  
- 必須設定 Visual Studio 專案進行遠端偵錯。
- 遠端電腦和 Visual Studio 電腦必須透過網路連線，或在直接透過 USB 或乙太網路纜線連接。 不支援透過網際網路偵錯。  
- 您必須[開啟開發人員模式](/windows/uwp/get-started/enable-your-device-for-development)Visual Studio 電腦和遠端電腦上。 
- 遠端電腦必須執行 Visual studio 遠端工具。 
  - 某些 Windows 10 版本開始，並自動執行遠端工具。 否則，請[安裝和執行 Visual Studio 遠端工具](#BKMK_download)。
  - Windows Mobile 10 裝置不需要或支援遠端工具。 

##  <a name="BKMK_ConnectVS"></a> 設定 Visual Studio 專案進行遠端偵錯
<a name="BKMK_DirectConnect"></a> 您使用專案**屬性**來指定要連接到遠端裝置。 設定不同的程式設計語言而定。 

> [!CAUTION]
> 根據預設，設定屬性頁**通用 （未加密的通訊協定）** 作為**驗證類型**對於 Windows 10 的遠端連線。 您可能需要設定**不需要驗證**連線到遠端偵錯工具。 **通用 （未加密的通訊協定）** 並**不需要驗證**通訊協定都不具有網路安全性，因此在開發和遠端電腦之間傳遞的資料是易受攻擊。 選擇這些驗證類型，只針對受信任的網路，您會確定沒有惡意流量的風險。 
>
>如果您選擇**Windows 驗證**for**驗證類型**，您必須偵錯時，登入到遠端電腦。 遠端偵錯工具也必須執行底下**Windows 驗證**模式中，使用相同的使用者帳戶做為 Visual Studio 電腦上。

###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> 設定C#或 Visual Basic 專案進行遠端偵錯  

1. 選取C#或 Visual Studio 中的 Visual Basic 專案**方案總管**，然後選取**屬性**圖示，並按下**Alt** + **請輸入**，或以滑鼠右鍵按一下並選擇 **屬性**。
  
1.  選取 [偵錯] 索引標籤。  
  
1.  底下**目標裝置**，選取**遠端機器**遠端電腦，或**裝置**直接連線的 Windows Mobile 10 裝置。  
  
1.  在遠端電腦，請輸入網路名稱或 IP 位址**遠端電腦**欄位，或選取**尋找**搜尋中的裝置[遠端連接 對話方塊中](#remote-connections)。 
    
    ![受管理的遠端偵錯專案屬性](../debugger/media/vsrun_managed_projprop_remote.png "Managed 偵錯專案屬性")  
    
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> 設定 JavaScript 或 c + + 專案進行遠端偵錯   
  
1.  選取 Visual Studio 中的 c + + 或 JavaScript 專案**方案總管**，然後選取**屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選擇 **屬性**。
  
1.  選取 [**偵錯**] 索引標籤。  
  
3.  底下**偵錯工具來啟動**，選取**遠端機器**遠端電腦，或**裝置**直接連線的 Windows Mobile 10 裝置。 
  
1.  遠端電腦中，輸入或選取的網路名稱或 IP 位址**電腦名稱** 欄位中或卸除並選取**尋找**搜尋中的裝置[遠端連線 對話方塊](#remote-connections). 

    ![遠端偵錯 c + + 專案屬性](../debugger/media/vsrun_cpp_projprop_remote.png "偵錯 c + + 專案屬性")
    
### <a name="remote-connections"></a> 使用 [遠端連線] 對話方塊

在 [**的遠端連線**] 對話方塊中，您可以搜尋特定的遠端電腦名稱或 IP 位址，或自動偵測連線選取的捨入箭號重新整理圖示。 對話方塊會搜尋本機子網路上的只有目前正在執行遠端偵錯工具裝置。 並非所有裝置，可以在偵測都到**的遠端連線** 對話方塊。 

 ![遠端連線 對話方塊](../debugger/media/vsrun_selectremotedebuggerdlg.png "遠端連線 對話方塊")  

>[!TIP]
>如果您不能依照名稱連接到遠端裝置，請嘗試使用其 IP 位址。 若要判斷 IP 位址，在遠端裝置上，輸入**ipconfig**在命令視窗中。 IP 位址會顯示為**IPv4 位址**。  
    
## <a name="BKMK_download"></a> 下載並安裝 Visual Studio 遠端工具

針對 Visual Studio 中偵錯遠端電腦上的應用程式，在遠端電腦必須執行遠端工具適用於 Visual Studio。 

- Windows Mobile 10 裝置不需要或不支援遠端工具。 
- Windows 10 電腦，執行建立者的更新 （版本 1703年） 和更新版本中，Windows 10 的 Xbox、 IoT 和 HoloLens 裝置的遠端工具時自動安裝您部署應用程式。 
- 預先建立者更新 Windows 10 電腦上您必須手動下載、 安裝和開始偵錯之前，遠端電腦上執行遠端工具。

**若要下載並安裝遠端工具：**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> 設定遠端工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> 遠端偵錯 UWP 應用程式 

遠端偵錯的運作方式相同本機偵錯。 

1. 在預先建立者更新版本的 Windows 10，請確定遠端的偵錯監視 (*msvsmon.exe*) 在遠端裝置上執行。  
   
1. Visual Studio 電腦上，確認正確的偵錯目標 (**遠端電腦**或是**裝置**) 會出現在工具列上的綠色箭號旁邊。 
   
1. 開始偵錯選取**偵錯** > **開始偵錯**、 按下**F5**，或選取工具列上的綠色箭號。 
   
   專案重新編譯，然後部署並啟動遠端裝置上。 偵錯工具在中斷點暫止執行，您可以逐步執行、 跳離程式碼。 
   
1. 如果有必要，請選取**偵錯** > **停止偵錯**或按**Shift**+**F5**停止偵錯和關閉遠端應用程式。
  
## <a name="see-also"></a>另請參閱  
 [進階遠端部署選項](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [使用 Visual Studio 測試 UWP 應用程式](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)   
 [在 Visual Studio 中對 UWP App 進行偵錯](debugging-windows-store-and-windows-universal-apps.md)
