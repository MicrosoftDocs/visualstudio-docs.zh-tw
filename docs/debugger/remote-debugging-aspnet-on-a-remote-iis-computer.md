---
title: 遠端偵錯 ASP.NET Core 在遠端 IIS 電腦上 |Microsoft Docs
description: 使用 Visual Studio 遠端偵錯程式，來對已部署至遠端 Internet Information Services 的 ASP.NET Core 應用程式進行 (IIS) 電腦的偵錯工具。
ms.custom: remotedebugging, SEO-VS-2020
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b288836b3868f561e86a801d5d26f7d59dd17535
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908266"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>遠端偵錯 ASP.NET Core 在 Visual Studio 的遠端 IIS 電腦上

若要對已部署至 IIS 的 ASP.NET Core 應用程式進行 debug，請在您部署應用程式的電腦上安裝並執行遠端工具，然後從 Visual Studio 連接到執行中的應用程式。

![遠端偵錯程式元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南說明如何安裝和設定 Visual Studio ASP.NET Core、將它部署到 IIS，以及從 Visual Studio 附加遠端偵錯程式。 若要進行遠端偵錯程式 ASP.NET 4.5.2，請參閱 [IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 您也可以使用 Azure 在 IIS 上部署和調試。 針對 Azure App Service，您可以使用 [快照偵錯工具](../debugger/debug-live-azure-applications.md) 或 [從伺服器總管附加偵錯工具](../debugger/remote-debugging-azure.md)，輕鬆地在預先設定的 IIS 實例和遠端偵錯程式上部署和偵錯工具。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"
需要 Visual Studio 2019，才能遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
需要 Visual Studio 2017，才能遵循本文中所示的步驟。
::: moniker-end

這些程式已經過這些伺服器設定的測試：
* Windows Server 2012 R2 和 IIS 8
* Windows Server 2016 和 IIS 10
* Windows Server 2019 和 IIS 10

## <a name="network-requirements"></a>網路需求

不支援透過 proxy 連線的兩部電腦之間的偵錯工具。 不建議透過高延遲或低頻寬的連線（例如撥號網際網路，或透過網際網路跨國家/地區）進行偵錯工具，且可能會失敗或使其變慢。 如需完整的需求清單，請參閱 [需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="app-already-running-in-iis"></a>應用程式已在 IIS 中執行？

本文包含在 Windows server 上設定 IIS 的基本設定，以及從 Visual Studio 部署應用程式的步驟。 包含這些步驟是為了確保伺服器已安裝必要元件、應用程式可以正確執行，而且您已準備好進行遠端偵錯程式。

* 如果您的應用程式是在 IIS 中執行，而您只想要下載遠端偵錯程式並啟動偵錯工具，請移至 [下載並在 Windows Server 上安裝遠端工具](#BKMK_msvsmon)。

* 如果您想要協助確保您的應用程式已在 IIS 中正確設定、部署及執行，以便您可以進行偵錯工具，請依照本主題中的所有步驟進行。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上建立 ASP.NET Core 應用程式

1. 建立新的 ASP.NET Core Web 應用程式。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，輸入 **Ctrl + Q** 以開啟 [搜尋] 方塊，輸入 **asp.net**，選擇 [ **範本**]，然後選擇 [ **建立新的 ASP.NET Core Web 應用程式**]。 在出現的對話方塊中，將專案命名為 **MyASPApp**，然後選擇 [ **建立**]。 接著，選擇 [ **Web 應用程式] (模型-視圖控制器)**]，然後選擇 [ **建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇 [檔案] **> [新的 > 專案**]，然後選取 [ **Visual c # > Web > ASP.NET Core web 應用程式**]。 在 [ASP.NET Core 範本] 區段中，選取 [ **Web 應用程式] ([模型-視圖控制器])**。 確定已選取 [ASP.NET Core 2.1]，但未選取 [ **啟用 Docker 支援** ]，並將 [ **驗證** ] 設定為 [ **無驗證**]。 將專案命名為 **MyASPApp**。
    ::: moniker-end

4. 開啟 About.cshtml.cs 檔案，並在 `OnGet` 舊版範本的方法 (中設定中斷點，改為開啟 HomeController.cs，然後在方法) 中設定中斷點 `About()` 。

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> 在 Windows Server 上安裝和設定 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中啟用增強式安全性設定 () 預設會啟用該設定，則您可能需要將某些網域新增為信任的網站，讓您能夠下載某些 web 伺服器元件。 前往 [ **網際網路選項] > 安全性 > 信任的網站 > 網站**]，以新增信任的網站。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，可能會取得授與許可權以載入各種網站腳本和資源的要求。 其中有些資源並非必要，但為了簡化此程式，請在出現提示時按一下 [ **加入** ]。

## <a name="install-aspnet-core-on-windows-server"></a>在 Windows Server 上安裝 ASP.NET Core

1. 在主控系統上安裝 .NET Core 裝載套件組合。 套件組合會安裝 .NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 如需更深入的指示，請參閱 [發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    若是 .NET Core 3，請安裝 [.Net Core 裝載](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)套件組合。
    若是 .NET Core 2，請安裝 [.Net Core Windows Server 裝載](https://aka.ms/dotnetcore-2-windowshosting)。

    > [!NOTE]
    > 如果系統沒有網際網路連線，請先取得並安裝 *[Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* 可轉散發套件，再安裝 .Net Core Windows Server 裝載套件組合。

3. 重新開機系統 (或執行 **net stop was/y** ，然後從命令提示字元執行 **net start w3svc** ，以挑選系統路徑的變更) 。

## <a name="choose-a-deployment-option"></a>選擇部署選項

如果您需要協助將應用程式部署至 IIS，請考慮下列選項：

* 在 IIS 中建立發行設定檔，並將設定匯入 Visual Studio 來進行部署。 在某些案例中，這是部署應用程式的快速方式。 當您建立發行設定檔案時，系統會自動在 IIS 中設定許可權。

* 藉由發行至本機資料夾並將輸出依慣用方法複製到 IIS 上備妥的應用程式資料夾來進行部署。

## <a name="optional-deploy-using-a-publish-settings-file"></a> (選擇性) 使用發佈設定檔部署

您可以使用此選項建立發佈設定檔案，並將它匯入 Visual Studio。

> [!NOTE]
> 此部署方法會使用必須安裝在伺服器上的 Web Deploy。 如果您想要手動設定 Web Deploy 而不是匯入設定，則可以安裝 Web Deploy 3.6，而不是裝載伺服器的 Web Deploy 3.6。 但是，如果您手動設定 Web Deploy，就必須確定伺服器上的應用程式資料夾已設定正確的值和許可權， (請參閱 [設定 ASP.NET 網站](#BKMK_deploy_asp_net)) 。

### <a name="configure-the-aspnet-core-web-site"></a>設定 ASP.NET Core 網站

1. 在 [IIS 管理員] 的左窗格中，選取 [ **連接**] 底下的 [ **應用程式** 集區]。 開啟 **DefaultAppPool** ，並將 **.net CLR 版本** 設為 [ **沒有 Managed 程式碼**]。 這是 ASP.NET Core 的必要項。 預設的網站會使用 DefaultAppPool。

2. 停止並重新啟動 DefaultAppPool。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>在 Windows Server 上安裝和設定主控伺服器的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果應用程式不是從 Visual Studio 啟動，請在 IIS 中啟動應用程式，以確認它是否正確執行。 針對 ASP.NET Core，您也必須確定 **DefaultAppPool** 的 [應用程式集區] 欄位設定為 [ **沒有 Managed 程式碼**]。

1. 在 [**設定**] 對話方塊中，按一下 [**下一步]** 來啟用偵錯工具，選擇 **調試** 程式設定，然後選擇 [檔案 **發行** 選項] 下的 [**移除目的地的其他** 檔案]。

    > [!IMPORTANT]
    > 如果您選擇發行設定，就會在發行時停用 *web.config* 檔案中的調試。

1. 按一下 [ **儲存** ]，然後重新發佈應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a> (選擇性) 透過發行至本機資料夾來部署

如果您想要使用 PowerShell、RoboCopy 將應用程式複製到 IIS，或想要手動複製檔案，您可以使用此選項來部署應用程式。

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> 在 Windows Server 電腦上設定 ASP.NET Core 網站

1. 開啟 Windows 檔案總管，然後建立新的資料夾 **C:\Publish**，您稍後將在其中部署 ASP.NET Core 專案。

2. 如果尚未開啟，請開啟 **Internet Information Services (IIS) 管理員**。  (在 [伺服器管理員] 的左窗格中，選取 [ **IIS**]。 以滑鼠右鍵按一下伺服器，然後選取 [Internet Information Services (IIS) 管理員]。)

3. 在左窗格的 [ **連接** ] 底下，移至 [ **網站**]。

4. 選取 [ **預設的網站**]，選擇 [ **基本設定**]，並將 [ **實體路徑** ] 設定為 [ **C:\Publish**]。

4. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

5. 將 [ **別名** ] 欄位設定為 **MyASPApp**、接受預設的應用程式集區 (**DefaultAppPool**) ，然後將 **實體路徑** 設定為 **C:\Publish**。

6. 在 [ **連接**] 底下，選取 [ **應用程式** 集區]。 開啟 **DefaultAppPool** ，並將 [應用程式集區] 欄位設定為 [ **沒有 Managed 程式碼**]。

7. 在 [IIS 管理員] 中的新網站上按一下滑鼠右鍵，選擇 [ **編輯許可權**]，並確定 [IUSR]、[IIS_IUSRS] 或設定為存取 web 應用程式的使用者，都是具有 [讀取] & [執行] 許可權的授權使用者。

    如果您沒有看到其中一個使用者具有存取權，請執行下列步驟，將 IUSR 新增為具有 Read & Execute 許可權的使用者。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>從 Visual Studio 發佈到本機資料夾，以發佈和部署應用程式

您也可以使用檔案系統或其他工具來發佈和部署應用程式。

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

1. 如果您要遵循本文中的所有步驟，請在 Visual Studio 電腦上開啟您嘗試 (**MyASPApp** 的解決方案) 。
2. 在 Visual Studio 中，按一下 [ **Debug > 附加至進程** ] (Ctrl + Alt + P) 。

    > [!TIP]
    > 在 Visual Studio 2017 和更新版本中，您可以使用 **Debug > 重新附加至進程 ...** (Shift + Alt + P) ，重新附加至您先前附加的相同進程。

3. 將 [辨識符號] 欄位設定為 **\<remote computer name>** ，然後按 **enter** 鍵。

    確認 Visual Studio 將必要的埠新增至電腦名稱稱，其格式如下： **\<remote computer name> :p 從排序 o**

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 上，您應該會看到 **\<remote computer name> ： 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 上，您應該會看到 **\<remote computer name> ： 4022**
    ::: moniker-end
    需要端口。 如果您沒有看到埠號碼，請以手動方式新增。

4. 按一下 [重新整理]。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您看不到任何進程，請嘗試使用 IP 位址，而不是遠端電腦名稱稱 (需要) 埠。 您可以 `ipconfig` 在命令列中使用，以取得 IPv4 位址。

    如果您想要使用 [ **尋找** ] 按鈕，您可能需要在伺服器上 [開啟 UDP 埠 3702](#bkmk_openports) 。

5. 核取 [顯示所有使用者的處理序]  。

6. 輸入您的進程名稱的第一個字母，以快速尋找您的應用程式。

    * 如果您是在 IIS 上使用同 [進程裝載模型](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) ，請選取正確的 **w3wp.exe** 進程。 從 .NET Core 3 開始，這是預設值。

    * 否則，請選取 **dotnet.exe** 進程。  (這是跨進程裝載模型。 ) 

    如果您有多個進程顯示 *w3wp.exe* 或 *dotnet.exe*，請檢查 **使用者名稱** 資料行。 在某些情況下，[ **使用者名稱** ] 欄會顯示您的應用程式集區名稱，例如 **IIS APPPOOL\DefaultAppPool**。 如果您看到應用程式集區，但它並不是唯一的，請為您想要進行偵錯工具的應用程式實例建立新的命名應用程式集區，然後在 [ **使用者名稱** ] 資料行中輕鬆找到它。

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. 按一下 [附加] 。

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
* UDP 3702- (選擇性的) 探索埠可讓您在 Visual Studio 中附加至遠端偵錯程式時， **找到 [尋找** ] 按鈕。

1. 若要在 Windows Server 上開啟埠，請開啟 [ **開始** ] 功能表，搜尋 [ **具有 Advanced Security 的 Windows 防火牆**]。

2. 然後，選擇 [ **輸入規則] > 新規則 > 埠**]，然後按 **[下一步]**。  (UDP 3702，請改為選擇 **輸出規則** 。 ) 

3. 在 [ **特定本機埠**] 下，輸入埠號碼，然後按 **[下一步]**。

4. 按一下 **[允許連接**]，然後按 **[下一步]**。

5. 選取要為埠啟用的一或多個網路類型，然後按 **[下一步]**。

    您選取的類型必須包括遠端電腦連線的網路。
6. 針對輸入規則新增 (的名稱，例如 **IIS**、 **Web Deploy** 或 **Msvsmon**) ，然後按一下 **[完成]**。

    您應該會在 [輸入規則] 或 [輸出規則] 清單中看到您的新規則。

    如果您想要設定 Windows 防火牆的詳細資訊，請參閱 [設定 Windows 防火牆以進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 為其他必要的埠建立其他規則。
