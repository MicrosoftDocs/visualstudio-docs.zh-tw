---
title: 遠端偵錯 ASP.NET 在 IIS 7.5 的遠端電腦 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446084"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>遠端偵錯 IIS 的遠端電腦上的 ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以部署到 Windows Server 電腦與 IIS，ASP.NET Web 應用程式，並將它設定為遠端偵錯。 本指南說明如何安裝和設定 Visual Studio 2015 MVC 4.5.2 應用程式、 將它部署至 IIS，並從 Visual Studio 附加遠端偵錯工具。

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 10
* Windows Server 2008 R2 和 IIS 7.5

大部分的這篇文章中的資訊也適用於遠端偵錯 ASP.NET Core 應用程式時，不同之處在於部署 ASP.NET core 應用程式的不同，且需要額外的步驟。 若要部署至 IIS 的 ASP.NET Core 應用程式，您必須完成的所有區段[這篇文章](https://docs.asp.net/en/latest/publishing/iis.html)。

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Windows Server 電腦上安裝遠端偵錯工具的必要條件：

如需有關如何下載 Windows Server 電腦的遠端偵錯工具的指示，請參閱[遠端偵錯](../debugger/remote-debugging.md)。

若要執行遠端偵錯 ASP.NET 應用程式，您可以系統管理員身分執行遠端偵錯工具應用程式，或做為服務啟動遠端偵錯工具。 如需如何將遠端偵錯工具做為服務執行的詳細資料，請參閱 [Remote Debugging](../debugger/remote-debugging.md)。

安裝之後，請確定目標電腦上執行遠端偵錯工具。 (如果沒有，請搜尋**遠端偵錯工具**中**開始**功能表。 ) 的遠端偵錯工具視窗看起來像這樣。 （4020 是預設連接埠號碼）

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上建立應用程式  
  
1. 建立新的 MVC ASP.NET 應用程式。 ([檔案] / [新增] / [專案]，然後選取 [Visual C#] / [Web] / [ASP.NET Web 應用程式]  。 在 [ASP.NET 4.5.2]  範本區段中選取 [MVC] 。 請確定**雲端中的主機**未選取 [Azure] 區段底下。 將專案命名為**MyMVC**。)
1. 開啟 HomeController.cs 檔案，並在 `About()` 方法中設定中斷點。
1. 在 [方案總管] ，以滑鼠右鍵按一下專案節點，然後選取 [發行] 。
1. 針對 [選取發行目標] 選取 [自訂]  ，然後將設定檔命名為 **MyMVC**。 按 [ **下一步**]。
1. 在 [連接]  索引標籤上，設定 [發行方法]  欄位為 [檔案系統]  ，以及設定 [目標位置]  欄位為本機目錄。 按 [ **下一步**]。

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. 設定要 **偵錯**的組態。 按一下 [發行] 。

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    應用程式應該要發行至本機目錄。

## <a name="BKMK_deploy_asp_net"></a> 部署 Windows Server 的遠端電腦上的 ASP.NET 應用程式

 本節假設，Windows Server 電腦上已有啟用 IIS。 在 Windows Server 2012 R2，請參閱[IIS 組態](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration)啟用 IIS。 （您可以略過這篇文章中的其他章節除非您嘗試部署將 ASP.NET Core 應用程式。 針對 ASP.NET Core，遵循的步驟中的文章，以部署應用程式，而不是此處所述的步驟。）
1. 安裝 ASP.NET 使用 Web 平台元件以安裝 ASP.NET 4.5 (從 [Windows Server 2012 R2 中的 [伺服器] 節點中，選擇**取得新的 Web 平台元件**]，然後搜尋適用於 ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    在 Windows Server 2008 R2 上安裝 ASP.NET 4，改為使用下列命令： **C:\Windows\Microsoft.NET\Framework(64)\v4.0.30319\aspnet_regiis.exe -ir**
1. 將 ASP.NET 專案目錄從 Visual Studio 電腦複製到在 Windows 伺服器電腦上的本機目錄 (我們將稱之為 **C:\Publish**)。 您可以手動複製專案，請使用 Xcopy、 Web Deploy、 Robocopy、 Powershell 或其他選項。

    > [!CAUTION]
    > 如果您需要對程式碼或重建的變更，您必須重新發行，並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。
1. 請確定 web.config 檔案會列出 .NET Framework 的正確版本。  比方說，Windows Server 2008 R2 上的預設安裝的.NET Framework 版本是 4.0.30319，但是我們建立的是 ASP.NET 4.5.2 版本。 如果 ASP.NET 4.0 應用程式正在執行 Windows Server 電腦上，您需要變更的版本：
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. 開啟 [Internet Information Services (IIS) 管理員]  並移至 [網站] 。
1. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。
1. 設定**別名**欄位設為**MyMVC** ，讓應用程式集區欄位**ASP.NET v4.0** （ASP.NET 4.5 不是應用程式集區的選項）。 將 [實體路徑]  設定為 **C:\Publish** (您複製 ASP.NET 專案目錄的地方)。

    >[!NOTE] 
    > ASP.NET Core 應用程式，將應用程式集區欄位設**沒有 Managed 程式碼**。
1. 測試部署，以滑鼠右鍵按一下**Default Web Site** ，然後選取**瀏覽**。
    如果您已成功部署應用程式，您會看到網頁。

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. 在 Visual Studio 電腦上開啟 [MyMVC]  方案。
1. 在 Visual Studio 中，按一下**偵錯] / [附加至處理序**(**Ctrl + Alt + P**)。
1. [限定詞] 欄位設定為 **\<遠端電腦名稱>:4020**。
1. 按一下 [重新整理]。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您沒有看到任何處理程序，請嘗試使用的 IP 位址，而不 （連接埠是必要的） 遠端電腦名稱。 使用`ipconfig`取得 IPv4 位址的命令列。
1. 核取 [顯示所有使用者的處理序]  。
1. 尋找 **w3wp.exe** ，然後按一下 [附加] 。

     若要快速找到處理序名稱，輸入程序的第一個字母。
     
    >[!NOTE]
    > ASP.NET Core 應用程式中，選擇 dnx.exe 程序，而不是 w3wp.exe。 （即將推出的版本中可能會變更此處理序名稱）。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. 開啟遠端電腦的網站。 在瀏覽器中，移至 **http://\<遠端電腦名稱>**。
    
    您應該會看到 ASP.NET 網頁。
1. 在 ASP.NET 網頁上，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。
