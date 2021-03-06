---
title: 在 IIS 電腦上對 ASP.NET 進行遠端偵錯
description: 瞭解如何安裝和設定 Visual Studio ASP.NET MVC 4.5.2 應用程式、將其部署至 IIS，以及從 Visual Studio 附加遠端偵錯程式。
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 104927d42f7ec68e43686278042c0712bb3c875e
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102250077"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯

若要對已部署至 IIS 的 ASP.NET 應用程式進行偵錯工具，請在您部署應用程式的電腦上安裝並執行遠端工具，然後從 Visual Studio 附加到執行中的應用程式。

![遠端偵錯程式元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南說明如何安裝和設定 Visual Studio ASP.NET MVC 4.5.2 應用程式、將其部署至 IIS，以及從 Visual Studio 附加遠端偵錯程式。

> [!NOTE]
> 若要改為遠端 debug ASP.NET Core，請參閱 [IIS 電腦上的遠端 debug ASP.NET core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。 針對 Azure App Service，您可以使用 [快照偵錯工具](../debugger/debug-live-azure-applications.md) ( .net 4.6.1 所需) 或 [從 Server Explorer 附加偵錯工具](../debugger/remote-debugging-azure.md)，輕鬆地在預先設定的 IIS 實例上進行部署和偵錯工具。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"
需要有 Visual Studio 2019，才能遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
需要有 Visual Studio 2017，才能遵循本文中所示的步驟。
::: moniker-end

這些程式已經過這些伺服器設定的測試：

* Windows server 2012 R2 和 IIS 8 (針對 Windows Server 2008 R2，伺服器步驟不同) 

## <a name="network-requirements"></a>網路需求

從 Windows Server 2008 Service Pack 2 開始，Windows Server 支援遠端偵錯程式。 如需完整的需求清單，請參閱 [需求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援透過 proxy 連線的兩部電腦之間的偵錯工具。 不建議透過高延遲或低頻寬的連線（例如撥號網際網路，或透過網際網路跨國家/地區）進行偵錯工具，且可能會失敗或使其變慢。

## <a name="app-already-running-in-iis"></a>應用程式已在 IIS 中執行？

本文包含在 Windows server 上設定 IIS 的基本設定，以及從 Visual Studio 部署應用程式的步驟。 包含這些步驟是為了確保伺服器已安裝必要元件、應用程式可以正確執行，而且您已準備好進行遠端偵錯程式。

* 如果您的應用程式是在 IIS 中執行，而您只想要下載遠端偵錯程式並啟動偵錯工具，請移至 [下載並在 Windows Server 上安裝遠端工具](#BKMK_msvsmon)。

* 如果您想要協助確保您的應用程式已在 IIS 中正確設定、部署及執行，以便您可以進行偵錯工具，請依照本主題中的所有步驟進行。

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上建立 ASP.NET 4.5.2 應用程式

1. 建立新的 MVC ASP.NET 應用程式。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，輸入 **Ctrl + Q** 以開啟 [搜尋] 方塊，輸入 **asp.net**，選擇 [ **範本**]，然後選擇 [ **建立新的 ASP.NET Web 應用程式 ( .net Framework)**。 在出現的對話方塊中，將專案命名為 **MyASPApp**，然後選擇 [ **建立**]。 選取 [ **MVC** ]，然後選擇 [ **建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    若要在 Visual Studio 2017 中這樣做，請選擇 [檔案 **> 新的 > 專案**]，然後選取 [ **Visual c # > Web > ASP.NET web 應用程式**]。 在 [ASP.NET 4.5.2]  範本區段中選取 [MVC] 。 請確定未選取 [ **啟用 Docker 支援** ]，並將 [ **驗證** ] 設定為 [ **無驗證**]。 將專案命名為 **MyASPApp**。 ) 
    ::: moniker-end

2. 開啟  *HomeController.cs* 檔案，並在方法中設定中斷點 `About()` 。

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> 在 Windows Server 上安裝和設定 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中啟用增強式安全性設定 (預設會啟用此功能) ，您可能需要將某些網域新增為信任的網站，讓您能夠下載某些 web 伺服器元件。 前往 [ **網際網路選項] > 安全性 > 信任的網站 > 網站**]，以新增信任的網站。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，可能會取得授與許可權以載入各種網站腳本和資源的要求。 其中有些資源並非必要，但為了簡化此程式，請在出現提示時按一下 [ **加入** ]。

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a> 在 Windows Server 上安裝 ASP.NET 4。5

如果您想要在 IIS 上安裝 ASP.NET 的詳細資訊，請參閱 [使用 ASP.NET 3.5 和 ASP.NET 4.5 的 iis 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

1. 在 [伺服器管理員] 的左窗格中，選取 [ **IIS**]。 以滑鼠右鍵按一下伺服器，然後選取 [ **Internet Information Services (IIS) 管理員**]。

1. 使用 (WebPI) 的 Web Platform Installer，從 Windows Server 2012 R2 的伺服器節點安裝 ASP.NET 4.5 (，選擇 [ **取得新的 Web 平臺元件** ]，然後搜尋 ASP.NET) 

    ![Web Platform Installer 5.0 的螢幕擷取畫面，其中顯示 asp.net 的搜尋結果，其中 web platform 元件 IIS： ASP.NET 4.5 以紅色圓圈表示。](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > 如果您使用的是 Windows Server 2008 R2，請使用下列命令來安裝 ASP.NET 4：

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 重新開機系統 (或執行 **net stop was/y** ，然後從命令提示字元執行 **net start w3svc** ，以挑選系統路徑的變更) 。

## <a name="choose-a-deployment-option"></a>選擇部署選項

如果您需要協助將應用程式部署至 IIS，請考慮下列選項：

* 在 IIS 中建立發行設定檔，並在 Visual Studio 中匯入設定來進行部署。 在某些案例中，這是部署應用程式的快速方式。 當您建立發行設定檔案時，系統會自動在 IIS 中設定許可權。

* 藉由發行至本機資料夾並將輸出依慣用方法複製到 IIS 上備妥的應用程式資料夾來進行部署。

## <a name="optional-deploy-using-a-publish-settings-file"></a> (選擇性) 使用發佈設定檔部署

您可以使用此選項建立發佈設定檔案，並將它匯入至 Visual Studio。

> [!NOTE]
> 此部署方法會使用必須安裝在伺服器上的 Web Deploy。 如果您想要手動設定 Web Deploy 而不是匯入設定，則可以為主控伺服器安裝 Web Deploy 3.6，而不是 Web Deploy 3.6。 但是，如果您手動設定 Web Deploy，您將需要確定伺服器上的應用程式資料夾已設定正確的值和許可權 (請參閱 [設定 ASP.NET 網站](#BKMK_deploy_asp_net)) 。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>在 Windows Server 上安裝和設定主控伺服器的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果應用程式不是從 Visual Studio 啟動，請在 IIS 中啟動應用程式。

1. 切換至 debug 設定。

   ::: moniker range=">=vs-2019"
   選擇 [ **編輯** ] 以編輯設定檔，然後選擇 [ **設定**]。 選擇 [ **Debug** ] 設定，然後選擇 [檔案 **發行** 選項] 下的 [**移除目的地的其他** 檔案]。
   ::: moniker-end
   ::: moniker range="vs-2017"
   在 [**設定**] 對話方塊中，按一下 [**下一步]** 來啟用偵錯工具，選擇 **調試** 程式設定，然後選擇 [檔案 **發行** 選項] 下的 [**移除目的地的其他** 檔案]。
   ::: moniker-end

   > [!IMPORTANT]
   > 如果您選擇發行設定，就會在發行時停用 *web.config* 檔案中的調試。

1. 按一下 [ **儲存** ]，然後重新發佈應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a> (選擇性) 透過發行至本機資料夾來部署

如果您想要使用 PowerShell、RoboCopy 將應用程式複製到 IIS，或想要手動複製檔案，您可以使用此選項來部署應用程式。

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> 在 Windows Server 電腦上設定 ASP.NET 網站

1. 開啟 Windows Explorer，然後建立新的資料夾 **C:\Publish**，您稍後將在其中部署 ASP.NET 專案。

2. 如果尚未開啟，請開啟 **Internet Information Services (IIS) 管理員**。  (在 [伺服器管理員] 的左窗格中，選取 [ **IIS**]。 以滑鼠右鍵按一下伺服器，然後選取 [Internet Information Services (IIS) 管理員]。)

3. 在左窗格的 [ **連接** ] 底下，移至 [ **網站**]。

4. 選取 [ **預設的網站**]，選擇 [ **基本設定**]，並將 [ **實體路徑** ] 設定為 [ **C:\Publish**]。

5. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

6. 將 [ **別名** ] 欄位設定為 **MyASPApp**、接受預設的應用程式集區 (**DefaultAppPool**) ，然後將 **實體路徑** 設定為 **C:\Publish**。

7. 在 [ **連接**] 底下，選取 [ **應用程式** 集區]。 開啟 **DefaultAppPool** ，並將 [應用程式集區] 欄位設定為 **ASP.NET v4.0** (ASP.NET 4.5 不是應用程式集區) 的選項。

8. 在 [IIS 管理員] 中選取網站後，選擇 [ **編輯許可權**]，並確定 [使用者] 應用程式集區所設定的 [IUSR]、[IIS_IUSRS] 或 [使用者] 是具有讀取 & 執行許可權的授權使用者。 如果這些使用者都不存在，請以具有 Read & Execute 許可權的使用者的身份新增 IUSR。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>發行並部署應用程式，方法是從 Visual Studio 發行至本機資料夾

您也可以使用檔案系統或其他工具來發佈和部署應用程式。

1.  (ASP.NET 4.5.2) 確定 web.config 的檔案會列出正確的 .NET 版本。  例如，如果您的目標是 ASP.NET 4.5.2，請確定 web.config 中列出此版本。

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    例如，如果您安裝 ASP.NET 4 而不是4.5.2，版本應該是4.0。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> 下載並安裝 Windows Server 上的遠端工具

下載符合您 Visual Studio 版本的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> 在 Windows Server 上設定遠端偵錯程式

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要為其他使用者新增許可權，請變更遠端偵錯程式的驗證模式或埠號碼，請參閱 [設定遠端偵錯程式](../debugger/remote-debugging.md#configure_msvsmon)。

如需以服務形式執行遠端偵錯程式的詳細資訊，請參閱以 [服務形式執行遠端偵錯程式](../debugger/remote-debugging.md#bkmk_configureService)。

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> 從 Visual Studio 電腦附加至 ASP.NET 應用程式

1. 如果您遵循這篇文章中的步驟) ，請在 Visual Studio 電腦上開啟您嘗試 (**MyASPApp** 的解決方案。
2. 在 Visual Studio 中，按一下 [ **Debug > 附加至進程** ] (Ctrl + Alt + P) 。

    > [!TIP]
    > 在 Visual Studio 2017 和更新版本中，您可以使用 **Debug > 重新附加至進程 ...** (Shift + Alt + P) ，重新附加至您先前附加的相同進程。

3. 將 [辨識符號] 欄位設定為 **\<remote computer name>** ，然後按 **enter** 鍵。

    確認 Visual Studio 將必要的埠新增至電腦名稱稱，其格式如下： **\<remote computer name> :p 從排序 o**

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，您應該會看到 **\<remote computer name> ： 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，您應該會看到 **\<remote computer name> ： 4022**
    ::: moniker-end
    需要端口。 如果您沒有看到埠號碼，請以手動方式新增。

4. 按一下 [重新整理]。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您看不到任何進程，請嘗試使用 IP 位址，而不是遠端電腦名稱稱 (需要) 埠。 您可以 `ipconfig` 在命令列中使用，以取得 IPv4 位址。

5. 核取 [顯示所有使用者的處理序]  。

6. 輸入進程名稱的第一個字母，以快速找出 ASP.NET 4.5 **w3wp.exe** 。

    如果您有多個進程顯示 **w3wp.exe**，請檢查 **使用者名稱** 資料行。 在某些情況下，[ **使用者名稱** ] 欄會顯示您的應用程式集區名稱，例如 **IIS APPPOOL\DefaultAppPool**。 如果您看到應用程式集區，識別正確程式的簡單方法是為您要進行偵錯工具的應用程式實例建立新的命名應用程式集區，然後在 [ **使用者名稱** ] 資料行中輕鬆找到它。

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. 按一下 [**附加**]

8. 開啟遠端電腦的網站。 在瀏覽器中，移 **至 \<remote computer name> HTTP://**。

    您應該會看到 ASP.NET 網頁。
9. 在正在執行的 ASP.NET 應用程式中，按一下 [ **關於** ] 頁面的連結。

    應該在 Visual Studio 中叫用中斷點。

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 疑難排解在 Windows Server 上開啟必要的連接埠

在大部分的安裝中，ASP.NET 和遠端偵錯程式的安裝會開啟必要的埠。 不過，您可能需要確認埠已開啟。

> [!NOTE]
> 在 Azure VM 上，您必須透過 [網路安全性群組](/azure/virtual-machines/windows/nsg-quickstart-portal)開啟埠。

必要的埠：

* 80-IIS 的必要元件
::: moniker range=">=vs-2019"
* 4024-從 Visual Studio 2019 進行遠端偵錯程式的必要 (如需詳細資訊，請參閱 [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)) 。
::: moniker-end
::: moniker range="vs-2017"
* 4022-從 Visual Studio 2017 進行遠端偵錯程式的必要 (如需詳細資訊，請參閱 [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)) 。
::: moniker-end
* UDP 3702- (選擇性的) 探索埠可在您附加至 Visual Studio 中的遠端偵錯程式時，提供 [ **尋找** ] 按鈕。

1. 若要在 Windows Server 上開啟埠，請開啟 [ **開始** ] 功能表，搜尋 [ **具有 Advanced Security 的 Windows 防火牆**]。

2. 然後選擇 [ **輸入規則] > 新規則 > 埠**]。 選擇 **[下一步]** ，然後在 [ **特定本機埠**] 底下輸入埠號碼，再按 [ **下一步]**，再按 **[** 下一步]，再按 [下一步]，並為輸入規則新增 (**IIS**、 **Web Deploy** 或 **msvsmon**) 

    如果您想要設定 Windows 防火牆的詳細資訊，請參閱 [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 為其他必要的埠建立其他規則。