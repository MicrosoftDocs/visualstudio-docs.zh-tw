---
title: 在遠端電腦上的執行 Windows 市集應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f031e81911c9a36cd2c48abf7bd2b092bb5940f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886275"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>在遠端電腦上執行 Windows 市集應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

僅適用於 Windows] (../Image/windows_only_content.png"windows_only_content")  
  
 Visual Studio 遠端工具應用程式可讓您從執行 Visual Studio 的第二部電腦，執行、偵錯、程式碼剖析及測試在一個裝置上執行的 Windows 市集應用程式。 當 Visual Studio 電腦不支援 Windows 市集應用程式專屬功能 (如觸控、地理位置和實體方向) 時，在遠端裝置上執行就特別有效。 本主題說明設定和啟動遠端工作階段的程序。  
  
##  <a name="BKMK_In_this_topic"></a>本主題內容  
 您將學習：  
  
 [必要條件](#BKMK_Prerequisites)  
  
 [安全性](#BKMK_Security)  
  
 [如何直接連接到遠端裝置](#BKMK_DirectConnect)  
  
 [安裝遠端工具](#BKMK_Installing_the_Remote_Tools)  
  
 [啟動遠端偵錯工具監視](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [設定遠端偵錯工具](#BKMK_ConfigureRemoteDebugger)  
  
 [設定 Visual Studio 專案進行遠端偵錯](#BKMK_ConnectVS)  
  
- [選擇 C# 和 Visual Basic 專案的遠端裝置](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [選擇 JavaScript 和 C++ 專案的遠端裝置](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [執行遠端偵錯工作階段](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> 必要條件  
 若要在遠端裝置上偵錯：  
  
-   遠端裝置和 Visual Studio 電腦必須透過網路連接，或直接透過乙太網路纜線連接。 不支援透過網際網路偵錯。  
  
-   遠端裝置上必須安裝開發人員授權。  
  
-   遠端裝置必須正在執行遠端偵錯元件。  
  
-   您必須是遠端裝置的系統管理員，才能在安裝時設定防火牆。 您必須具有遠端裝置的使用者存取權，才能執行或連接到遠端偵錯工具。  
  
##  <a name="BKMK_Security"></a> 安全性  
 根據預設，遠端偵錯工具會使用 Windows 驗證。  
  
> [!WARNING]
>  您也可以選擇在 [非驗證] 模式下執行遠端偵錯工具，但非常不建議您使用這個模式。 在此模式中執行時不具有網路安全性。 只有在確定網路沒有面臨惡意或攻擊流量的風險時，才能選擇非驗證模式。  
  
##  <a name="BKMK_DirectConnect"></a> 如何直接連接到遠端裝置  
 若要直接連接到遠端裝置，請使用標準乙太網路纜線將 Visual Studio 電腦連接到此裝置。 如果裝置沒有乙太網路連接埠，您可以使用 USB 乙太網路轉接線連接到纜線。  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> 安裝遠端工具  
  
> [!NOTE]
>  **版本和更新**  
>   
>  **Visual Studio 2015 遠端工具** 不支援舊版 Visual Studio。  
>   
>  我們建議您安裝 Visual Studio 2015 遠端工具更新版本，以符合您的 Visual Studio 安裝更新版本。  
>   
>  VS 偵錯工具與 VS 2015 版本和 VS 2015 遠端工具的任何組合相容。 不過，Visual Studio 的最新功能要求 Visual Studio 和遠端工具必須是最新版本。  
>   
>  其他診斷工具可能要求遠端工具和 Visual Studio 必須是相同版本。  
  
 **在遠端裝置上安裝遠端偵錯元件**  
  
 若要執行或儲存遠端工具的安裝程式，選擇符合您 Visual Studio 版本的此資料表中的其中一個連結：  
  
|版本|連結|注意|
|-|-|-|
|Visual Studio 2015 Update 3|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|出現提示時，加入免費的 Visual Studio Dev Essentials 群組，或您只可以使用有效的 Visual Studio 訂用帳戶登入。 然後重新開啟連結如有必要。 一律下載比對 (x，x86、 x64 或 ARM 版本） 您裝置的作業系統版本|
|Visual Studio 2015 （舊版）|[遠端工具](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|出現提示時，加入免費的 Visual Studio Dev Essentials 群組，或您只可以使用有效的 Visual Studio 訂用帳戶登入。 然後重新開啟連結如有必要。一律下載比對 (x，x86、 x64 或 ARM 版本） 您裝置的作業系統版本|
|Visual Studio 2013|[遠端工具](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|下載 Visual Studio 2013 文件中的頁面|
  
 您可以選擇下載安裝程式，也可以立即執行。 當您執行安裝程式時，接受使用者合約，然後選擇 [ **安裝**]。  
  
 根據預設，遠端偵錯元件安裝在 **C:\Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger** 資料夾中。  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> 啟動遠端偵錯工具監視  
  
> [!NOTE]
>  由於遠端偵錯工具會設定防火牆，允許與 Visual Studio 主機通訊，因此您第一次啟動遠端偵錯工具時，必須是遠端裝置上的系統管理員。  
  
 安裝遠端工具之後，請選擇 [ **開始** ] 畫面的 [ **遠端偵錯工具** ]。 [ **遠端偵錯組態** ] 會在您第一次啟動遠端偵錯工具時出現。  
  
 在 [ **遠端偵錯組態** ] 對話方塊上：  
  
1.  如果沒有安裝 Windows Web 服務應用程式開發介面，請選擇 [ **安裝**]。  
  
2.  在 [ **設定 Windows 防火牆** ] 群組中，選擇您要允許連接的網路。 只會啟用裝置目前連接的網路。 您必須至少選擇一個網路。  
  
3.  選擇 [ **設定遠端偵錯** ] 以設定防火牆選項並啟動遠端偵錯工具。  開啟 [ **Visual Studio 遠端偵錯監視** ] 對話方塊，授與使用者遠端工具的權限及設定其他進階選項。  
  
4.  [ **Visual Studio 遠端偵錯監視** ] 對話方塊隨即出現。 您可以從這個對話方塊中，授與使用者遠端工具的權限和設定其他進階選項。  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> 設定遠端偵錯工具  
 使用兩種工具可以修改遠端偵錯工具的組態。  
  
1. 在 [ **Visual Studio 遠端偵錯監視** ] 的 [ **工具**] 功能表上：  
  
   1.  選擇 [ **選項** ] 變更遠端偵錯工具的連接埠號碼、驗證模式或逾時間隔。  
  
   2.  選擇 [ **權限** ] 新增或移除具有遠端偵錯權限的使用者。  
  
       > [!NOTE]
       >  每一個從遠端進行偵錯的使用者帳戶都必須具有權限。  
  
   使用 [ **遠端偵錯工具組態精靈** ] 設定遠端偵錯工具的進階選項。 若要開啟精靈，請選擇 [開始] 畫面上的 [ **遠端偵錯工具組態精靈** ]。  
  
2. 您可以在 [ **設定 Visual Studio 遠端偵錯工具** ] 頁面上選擇將遠端偵錯工具當做服務執行。 大部分情況下不需要當做服務執行。  
  
3. 在 [ **設定 Windows 防火牆進行偵錯** ] 頁面上，您可以新增或移除遠端偵錯工具要連接的網路類型。 只會啟用裝置目前連接的網路。 您必須至少選擇一個網路。  
  
##  <a name="BKMK_ConnectVS"></a> 設定 Visual Studio 專案進行遠端偵錯  
 您可在專案的屬性中指定要連接的遠端裝置。 此程序會因程式語言而有所差異。 您可以輸入遠端裝置的網路名稱，也可以從 [選取遠端偵錯工具連接] 對話方塊進行選取。  
  
 ![選取遠端偵錯工具連接 對話方塊](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 此對話方塊會列出 Visual Studio 電腦的區域子網路上的裝置，以及執行遠端偵錯工具的裝置。  
  
> [!TIP]
>  如果無法順利連接到遠端裝置，請嘗試輸入裝置的 IP 位址。 若要判斷裝置的 IP 位址，請開啟命令視窗，然後輸入 **ipconfig**。 IP 位址會列示為 **IPv4 Address**。  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> 選擇 C# 和 Visual Basic 專案的遠端裝置  
 ![受管理的遠端偵錯專案屬性](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  在 [方案總管] 中選取專案名稱，然後從捷徑功能表選擇 [ **屬性** ]。  
  
2.  選取 [ **偵錯**]。  
  
3.  從 [ **目標裝置** ] 清單選擇 [ **遠端電腦** ]。  
  
4.  在 [ **遠端電腦** ] 方塊中輸入遠端裝置的網路名稱，或選擇 [ **尋找** ]，從 [ **選取遠端偵錯工具連接** ] 對話方塊選擇裝置。  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> 選擇 JavaScript 和 C++ 專案的遠端裝置  
 ![C&#43; &#43;的專案進行遠端偵錯的屬性](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  在 [方案總管] 中選取專案名稱，然後從捷徑功能表選擇 [ **屬性** ]。  
  
2.  展開 [ **組態屬性** ] 節點，然後選取 [ **偵錯**]。  
  
3.  從 [ **要啟動的偵錯工具** ] 清單選擇 [ **遠端偵錯工具** ]。  
  
4.  在 [ **電腦名稱** ] 方塊中輸入遠端裝置的網路名稱，或選擇方塊中的向下鍵，從 [ **選取遠端偵錯工具連接** ] 對話方塊選擇裝置。  
  
##  <a name="BKMK_RunRemoteDebug"></a> 執行遠端偵錯工作階段  
 您啟動、停止及巡覽遠端偵錯工作階段的方式與您進行本機工作階段的方式相同。 在您開始偵錯之前，請確定遠端裝置上正在執行遠端偵錯監視。  
  
 然後在 [ **偵錯** ] 功能表上選擇 [ **開始偵錯** ] (鍵盤：F5)。 專案會重新編譯，然後部署到遠端裝置並且啟動。 偵錯工具會在中斷點暫停執行，而您可以逐步執行、跳過和跳離您的程式碼。 選擇 [ **停止偵錯** ] 即可結束偵錯工作階段，並關閉遠端應用程式。 如需詳細資訊，請參閱 <<c0> [ 偵錯在 Visual Studio 中的應用程式](../debugger/debug-store-apps-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Studio 測試市集應用程式](../test/testing-store-apps-with-visual-studio.md)   
 [在 Visual Studio 中偵錯應用程式](../debugger/debug-store-apps-in-visual-studio.md)



