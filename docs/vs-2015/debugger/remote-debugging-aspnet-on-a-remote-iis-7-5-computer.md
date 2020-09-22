---
title: 遠端偵錯 ASP.NET 在遠端 IIS 7.5 電腦上 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838994"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>在遠端 IIS 電腦上對 ASP.NET 進行遠端偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 IIS 將 ASP.NET Web 應用程式部署到 Windows Server 電腦，並設定它以進行遠端偵錯程式。 本指南說明如何安裝和設定 Visual Studio 2015 MVC 4.5.2 應用程式、將它部署至 IIS，以及從 Visual Studio 附加遠端偵錯程式。

這些程式已經過這些伺服器設定的測試：
* Windows Server 2012 R2 和 IIS 10
* Windows Server 2008 R2 和 IIS 7。5

本文中大部分的資訊也適用于遠端 ASP.NET Core 應用程式的偵錯工具，不同之處在于 ASP.NET Core 應用程式的部署不同，需要額外的步驟。 若要將 ASP.NET Core 應用程式部署至 IIS，您必須完成 [本文](https://docs.asp.net/en/latest/publishing/iis.html)的所有章節。

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>必要條件：在 Windows Server 電腦上安裝遠端偵錯程式

如需如何將遠端偵錯程式下載到 Windows Server 電腦的相關指示，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

若要執行 ASP.NET 應用程式的遠端偵錯程式，您可以用系統管理員身分執行遠端偵錯程式應用程式，或啟動遠端偵錯程式做為服務。 如需如何將遠端偵錯工具做為服務執行的詳細資料，請參閱 [Remote Debugging](../debugger/remote-debugging.md)。

安裝之後，請確定遠端偵錯程式正在目的電腦上執行。  (如果不是，請在 [**開始**] 功能表中搜尋**遠端偵錯程式**。 ) [遠端偵錯程式] 視窗如下所示。  (4020 是預設的埠號碼) 

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上建立應用程式  
  
1. 建立新的 MVC ASP.NET 應用程式。 ([檔案] / [新增] / [專案]****，然後選取 [Visual C#] / [Web] / [ASP.NET Web 應用程式] **** 。 在 [ASP.NET 4.5.2] **** 範本區段中選取 [MVC] ****。 請確定未在 Azure 區段底下選取 [ **雲端中的主機** ]。 將專案命名為 **MyMVC**。 ) 
1. 開啟 HomeController.cs 檔案，並在 `About()` 方法中設定中斷點。
1. 在 [方案總管] ****，以滑鼠右鍵按一下專案節點，然後選取 [發行] ****。
1. 針對 [選取發行目標] **** 選取 [自訂] **** ，然後將設定檔命名為 **MyMVC**。 按一下 [下一步]。
1. 在 [連接] **** 索引標籤上，設定 [發行方法] **** 欄位為 [檔案系統] **** ，以及設定 [目標位置] **** 欄位為本機目錄。 按一下 [下一步]。

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. 設定要 **偵錯**的組態。 按一下 [發佈] 。

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    應用程式應該要發行至本機目錄。

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> 在 Windows Server 遠端電腦上部署 ASP.NET 應用程式

 本節假設 Windows Server 電腦已啟用 IIS。 在 Windows Server 2012 R2 上，請參閱 [iis](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) 設定以啟用 iis。  (除非您嘗試部署 ASP.NET Core 應用程式，否則您可以略過本文的其他章節。 針對 ASP.NET Core，請遵循本文中的步驟來部署應用程式，而不是此處所述的步驟。 ) 
1. 安裝 ASP.NET 使用 Web Platform 元件，從 Windows Server 2012 R2 的伺服器節點安裝 ASP.NET 4.5 (，選擇 [ **取得新的 Web Platform 元件** ]，然後搜尋 ASP.NET) 

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    在 Windows Server 2008 R2 上，使用下列命令來安裝 ASP.NET 4：   **C:\Windows\Microsoft.NET\Framework (64) # A0-ir**
1. 將 ASP.NET 專案目錄從 Visual Studio 電腦複製到在 Windows 伺服器電腦上的本機目錄 (我們將稱之為 **C:\Publish**)。 您可以手動複製專案，使用 Xcopy、Web Deploy、Robocopy、Powershell 或其他選項。

    > [!CAUTION]
    > 如果您需要變更程式碼或重建，則必須重新發佈並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。
1. 請確定 web.config 檔案會列出 .NET Framework 的正確版本。  例如，預設安裝在 Windows Server 2008 R2 上的 .NET Framework 版本是4.0.30319，但我們已建立 ASP.NET 4.5.2 版本。 如果 Windows Server 電腦上正在執行 ASP.NET 4.0 應用程式，您需要變更版本：
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. 開啟 [Internet Information Services (IIS) 管理員] **** 並移至 [網站] ****。
1. 以滑鼠右鍵按一下 [預設的網站] **** 節點，並選取 [加入應用程式] ****。
1. 將 **別名** 欄位設定為 **MyMVC** ，並將 [應用程式集區] 欄位設定為 **ASP.NET 4.0** (ASP.NET 4.5 不是應用程式集區) 的選項。 將 [實體路徑] **** 設定為 **C:\Publish** (您複製 ASP.NET 專案目錄的地方)。

    >[!NOTE] 
    > 針對 ASP.NET Core 應用程式，將 [應用程式集區] 欄位設定為 [ **沒有 Managed 程式碼**]。
1. 以滑鼠右鍵按一下 [預設的 **網站** ]，然後選取 **[流覽]**，以測試部署。
    如果您已成功部署應用程式，您將會看到該網頁。

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. 在 Visual Studio 電腦上開啟 [MyMVC] **** 方案。
1. 在 Visual Studio 中，按一下 [ **Debug]/[附加至進程** ] (**Ctrl + Alt + P**) 。
1. 將 [辨識符號] 欄位設定為** \<remote computer name> ： 4020**。
1. 按一下 [重新整理]****。
    您應該會看到有些處理程序會出現在 [可使用的處理序] **** 視窗。

    如果您看不到任何進程，請嘗試使用 IP 位址，而不是遠端電腦名稱稱 (需要) 埠。 `ipconfig`在命令列中使用以取得 IPv4 位址。
1. 核取 [顯示所有使用者的處理序]  ****。
1. 尋找 **w3wp.exe** ，然後按一下 [附加] ****。

     若要快速尋找進程名稱，請輸入進程的第一個字母。
     
    >[!NOTE]
    > 對於 ASP.NET Core 應用程式，請選擇 dnx.exe 進程，而不是 w3wp.exe。  (在即將推出的版本中，此進程名稱可能會變更。 ) 

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. 開啟遠端電腦的網站。 在瀏覽器中，移**至 \<remote computer name> HTTP://**。
    
    您應該會看到 ASP.NET 網頁。
1. 在 [ASP.NET] 網頁中，按一下 [ **關於** ] 頁面的連結。

    應該在 Visual Studio 中叫用中斷點。
