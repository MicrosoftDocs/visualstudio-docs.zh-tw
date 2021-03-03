---
title: IIS 和 Azure 上的遠端偵錯 ASP.NET 核心 |Microsoft 檔
description: 瞭解如何安裝和設定 Visual Studio ASP.NET Core 應用程式、使用 Azure 將其部署至 IIS，以及從 Visual Studio 附加遠端偵錯程式。
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: d41beea47e8173170ea2d428b40bd7c7ed8ff67e
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684158"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio 中 Azure 上 IIS 的遠端 Debug ASP.NET Core

本指南說明如何安裝和設定 Visual Studio ASP.NET Core 應用程式、使用 Azure 將其部署至 IIS，以及從 Visual Studio 附加遠端偵錯程式。

在 Azure 上進行遠端偵錯的建議方式取決於您的案例：

* 若要在 Azure App Service 上進行 ASP.NET Core 的偵錯工具，請參閱 [使用快照偵錯工具來偵測 azure 應用程式](../debugger/debug-live-azure-applications.md)。 這是建議的方法。
* 若要使用更傳統的偵錯工具，在 Azure App Service 上進行 ASP.NET Core 的偵錯工具，請依照本主題中的步驟 (參閱 [Azure App service 上的遠端偵錯程式](#remote_debug_azure_app_service)) 一節。

    在此案例中，您必須將應用程式從 Visual Studio 部署至 Azure，但不需要手動安裝或設定 IIS 或遠端偵錯程式 (這些元件會以虛線表示) ，如下圖所示。

    ![顯示 Visual Studio、Azure App Service 和 ASP.NET 應用程式之間關聯性的圖表。 IIS 和遠端偵錯程式會以虛線表示。](../debugger/media/remote-debugger-azure-app-service.png)

* 若要在 Azure VM 上進行 IIS 的偵錯工具，請依照本主題中的步驟 (參閱 [AZURE vm 上的遠端偵錯程式](#remote_debug_azure_vm)) 一節。 這可讓您使用自訂的 IIS 設定，但設定和部署步驟會更複雜。

    針對 Azure VM，您必須將應用程式從 Visual Studio 部署到 Azure，而且您也需要手動安裝 IIS 角色和遠端偵錯程式，如下圖所示。

    ![顯示 Visual Studio、Azure VM 和 ASP.NET 應用程式之間關聯性的圖表。 IIS 和遠端偵錯程式會以實線表示。](../debugger/media/remote-debugger-azure-vm.png)

* 若要在 Azure Service Fabric 上進行 ASP.NET Core 的偵錯工具，請參閱 [debug a Remote Service fabric 應用程式](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)。

> [!WARNING]
> 當您完成本教學課程中的步驟時，請務必刪除您所建立的 Azure 資源。 如此一來，您就可以避免產生不必要的費用。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"
需要有 Visual Studio 2019，才能遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
需要有 Visual Studio 2017，才能遵循本文中所示的步驟。
::: moniker-end

### <a name="network-requirements"></a>網路需求

不支援透過 proxy 連線的兩部電腦之間的偵錯工具。 不建議透過高延遲或低頻寬的連線（例如撥號網際網路，或透過網際網路跨國家/地區）進行偵錯工具，且可能會失敗或可能會變慢。 如需完整的需求清單，請參閱 [需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上建立 ASP.NET Core 應用程式

1. 建立新的 ASP.NET Core Web 應用程式。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，選擇 [開始] 視窗中的 [ **建立新專案** ]。 如果 [開始] 視窗未開啟，請 **選擇 [** 檔案  >  **開始視窗]**。 輸入 **web 應用程式**，選擇 [ **c #** ] 作為語言，然後選擇 [ **ASP.NET Core web 應用程式] ([模型-視圖控制器])**，然後選擇 **[下一步]**。 在下一個畫面中，將專案命名為 **MyASPApp**，然後選擇 **[下一步]**。

    選擇建議的目標架構 ( .NET Core 3.1) 或 .NET 5，然後選擇 [ **建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇 [檔案 **> 新的 > 專案**]，然後選取 [ **Visual c # > Web > ASP.NET Core Web 應用程式**]。 在 [ASP.NET Core 範本] 區段中，選取 [ **Web 應用程式 (模型-視圖控制器)**。 確定已選取 [ASP.NET Core 2.1]，但未選取 [ **啟用 Docker 支援** ]，並將 [ **驗證** ] 設定為 [ **無驗證**]。 將專案命名為 **MyASPApp**。
    ::: moniker-end

1. 開啟 About.cshtml.cs 檔案，並在 `OnGet` 舊版範本的方法 (中設定中斷點，改為開啟 HomeController.cs，然後在方法) 中設定中斷點 `About()` 。

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Azure App Service 上的遠端 Debug ASP.NET Core

您可以從 Visual Studio 快速發佈應用程式，並將其偵測到完整布建的 IIS 實例。 不過，IIS 的設定是預設的，您無法自訂。 如需更詳細的指示，請參閱 [使用 Visual Studio 將 ASP.NET Core web 應用程式部署到 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。  (如果您需要自訂 IIS 的能力，請嘗試在 [AZURE VM](#remote_debug_azure_vm)上進行偵錯工具。 ) 

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>使用 Cloud Explorer 部署應用程式和遠端偵錯程式

1. 在 Visual Studio 中，以滑鼠右鍵按一下專案節點，然後選擇 [ **發行**]。

    如果您之前已設定任何發行設定檔，[發行] 窗格會隨即出現。 按一下 [ **新增設定檔**]。

1. 從 [**發行**] 對話方塊中選擇 [ **Azure App Service** ]，選取 [**建立新** 的]，並遵循提示來建立設定檔。

    如需詳細指示，請參閱[使用 Visual Studio 將 ASP.NET Core Web 應用程式部署至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

    ![發佈至 Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 在 [發行] 視窗中，選擇 [ **編輯** 設定] 並切換至調試設定，然後選擇 [ **發行**]。

   需要進行偵錯工具的偵錯工具。

1. 開啟 **cloud explorer** (**View**  >  **cloud explorer**) ，以滑鼠右鍵按一下 App Service 實例，然後選擇 [**附加偵錯工具**]。

   如果無法使用 [Cloud Explorer]，請改為開啟 [伺服器瀏覽器]。 然後，以滑鼠右鍵按一下 Server Explorer 中的 App Service 實例，然後選擇 [ **附加偵錯工具**]。

1. 在正在執行的 ASP.NET 應用程式中，按一下 [ **關於** ] 頁面的連結。

    應該在 Visual Studio 中叫用中斷點。

    大功告成！ 本主題的其餘步驟適用于 Azure VM 上的遠端偵錯程式。

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Azure VM 上的遠端 Debug ASP.NET Core

您可以建立適用于 Windows Server 的 Azure VM，然後安裝及設定 IIS 和其他所需的軟體元件。 這比部署至 Azure App Service 需要更多時間，而且需要您遵循本教學課程中的其餘步驟。

這些程式已經過這些伺服器設定的測試：
* Windows Server 2012 R2 和 IIS 8
* Windows Server 2016 和 IIS 10
* Windows Server 2019 和 IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>應用程式已在 Azure VM 上的 IIS 中執行？

本文包含在 Windows server 上設定 IIS 的基本設定，以及從 Visual Studio 部署應用程式的步驟。 包含這些步驟是為了確保伺服器已安裝必要元件、應用程式可以正確執行，而且您已準備好進行遠端偵錯程式。

* 如果您的應用程式是在 IIS 中執行，而您只想要下載遠端偵錯程式並啟動偵錯工具，請移至 [下載並在 Windows Server 上安裝遠端工具](#BKMK_msvsmon)。

* 如果您想要協助確保您的應用程式已在 IIS 中正確設定、部署及執行，以便您可以進行偵錯工具，請依照本主題中的所有步驟進行。

  * 開始之前，請遵循 [安裝和執行 IIS](/azure/virtual-machines/windows/quick-create-portal)中所述的所有步驟。

  * 當您在網路安全性群組中開啟埠80時，也請開啟遠端偵錯程式的 [正確埠](#bkmk_openports) (4024 或 4022) 。 如此一來，您就不需要稍後再開啟它。 如果您使用的是 Web Deploy，也請開啟埠8172。

### <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中啟用增強式安全性設定 (預設會啟用此功能) ，您可能需要將某些網域新增為信任的網站，讓您能夠下載某些 web 伺服器元件。 前往 [ **網際網路選項] > 安全性 > 信任的網站 > 網站**]，以新增信任的網站。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，可能會取得授與許可權以載入各種網站腳本和資源的要求。 其中有些資源並非必要，但為了簡化此程式，請在出現提示時按一下 [ **加入** ]。

### <a name="install-aspnet-core-on-windows-server"></a>在 Windows Server 上安裝 ASP.NET Core

1. 在主控系統上安裝 .NET Core 裝載套件組合。 套件組合會安裝 .NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 如需更深入的指示，請參閱 [發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    若是 .NET Core 3，請安裝 [.Net Core 裝載](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer)套件組合。
    若是 .NET Core 2，請安裝 [.Net Core Windows Server 裝載](https://aka.ms/dotnetcore-2-windowshosting)。

    > [!NOTE]
    > 如果系統沒有網際網路連線，請先取得並安裝 *[Microsoft Visual c + + 2015](https://www.microsoft.com/download/details.aspx?id=53840)* 可轉散發套件，再安裝 .Net Core Windows Server 裝載套件組合。

3. 重新開機系統 (或執行 **net stop was/y** ，然後從命令提示字元執行 **net start w3svc** ，以挑選系統路徑的變更) 。

## <a name="choose-a-deployment-option"></a>選擇部署選項

如果您需要協助將應用程式部署至 IIS，請考慮下列選項：

* 在 IIS 中建立發行設定檔，並在 Visual Studio 中匯入設定來進行部署。 在某些案例中，這是部署應用程式的快速方式。 當您建立發行設定檔案時，系統會自動在 IIS 中設定許可權。

* 藉由發行至本機資料夾並將輸出依慣用方法複製到 IIS 上備妥的應用程式資料夾來進行部署。

## <a name="optional-deploy-using-a-publish-settings-file"></a> (選擇性) 使用發佈設定檔部署

您可以使用此選項建立發佈設定檔案，並將它匯入至 Visual Studio。

> [!NOTE]
> 此部署方法會使用必須安裝在伺服器上的 Web Deploy。 如果您想要手動設定 Web Deploy 而不是匯入設定，則可以為主控伺服器安裝 Web Deploy 3.6，而不是 Web Deploy 3.6。 但是，如果您手動設定 Web Deploy，您將需要確定伺服器上的應用程式資料夾已設定正確的值和許可權 (請參閱 [設定 ASP.NET 網站](#BKMK_deploy_asp_net)) 。

### <a name="configure-the-aspnet-core-web-site"></a>設定 ASP.NET Core 網站

1. 在 [IIS 管理員] 的左窗格中，選取 [ **連接**] 底下的 [ **應用程式** 集區]。 開啟 **DefaultAppPool** ，並將 **.net CLR 版本** 設為 [ **沒有 Managed 程式碼**]。 這是 ASP.NET Core 的必要項。 預設的網站會使用 DefaultAppPool。

2. 停止並重新啟動 DefaultAppPool。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>在 Windows Server 上安裝和設定主控伺服器的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> 如果您重新開機 Azure VM，IP 位址可能會變更。

應用程式部署成功之後，它應該會自動啟動。 如果應用程式不是從 Visual Studio 啟動，請在 IIS 中啟動應用程式，以確認它是否正確執行。 針對 ASP.NET Core，您也必須確定 **DefaultAppPool** 的 [應用程式集區] 欄位設定為 [ **沒有 Managed 程式碼**]。

1. 在 [**設定**] 對話方塊中，按一下 [**下一步]** 來啟用偵錯工具，選擇 **調試** 程式設定，然後選擇 [檔案 **發行** 選項] 下的 [**移除目的地的其他** 檔案]。

    > [!IMPORTANT]
    > 如果您選擇發行設定，就會在發行時停用 *web.config* 檔案中的調試。

1. 按一下 [ **儲存** ]，然後重新發佈應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a> (選擇性) 透過發行至本機資料夾來部署

如果您想要使用 PowerShell、RoboCopy 將應用程式複製到 IIS，或想要手動複製檔案，您可以使用此選項來部署應用程式。

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> 在 Windows Server 電腦上設定 ASP.NET Core 網站

如果您要匯入發行設定，可以略過本節。

1. 開啟 [Internet Information Services (IIS) 管理員]  並移至 [網站] 。

2. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

3. 將 [**別名**] 欄位設定為 **MyASPApp** ，並將 [應用程式集區] 欄位設定為 [**沒有 Managed 程式碼** 設定 **C:\Publish** (的 **實體路徑**，您稍後將在其中部署 ASP.NET Core 專案) 。

4. 在 [IIS 管理員] 中選取網站後，選擇 [ **編輯許可權**]，並確定 [使用者] 應用程式集區所設定的 [IUSR]、[IIS_IUSRS] 或 [使用者] 是具有讀取 & 執行許可權的授權使用者。

    如果您沒有看到其中一個使用者具有存取權，請執行下列步驟，將 IUSR 新增為具有 Read & Execute 許可權的使用者。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a> (選擇性) 發行至 Visual Studio 中的本機資料夾，以發佈和部署應用程式

如果您不是使用 Web Deploy，您必須使用檔案系統或其他工具來發佈和部署應用程式。 您可以從使用檔案系統建立套件開始，然後以手動方式部署封裝，或使用 PowerShell、Robocopy 或 XCopy 等其他工具。 在本節中，我們假設您是在不使用 Web Deploy 的情況下，手動複製封裝。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> 下載並安裝 Windows Server 上的遠端工具

下載符合您 Visual Studio 版本的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> 在 Windows Server 上設定遠端偵錯程式

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要為其他使用者新增許可權，請變更遠端偵錯程式的驗證模式或埠號碼，請參閱 [設定遠端偵錯程式](../debugger/remote-debugging.md#configure_msvsmon)。

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> 從 Visual Studio 電腦附加至 ASP.NET 應用程式

1. 如果您遵循這篇文章中的步驟) ，請在 Visual Studio 電腦上開啟您嘗試 (**MyASPApp** 的解決方案。
2. 在 Visual Studio 中，按一下 [ **Debug > 附加至進程** ] (Ctrl + Alt + P) 。

    > [!TIP]
    > 在 Visual Studio 2017 和更新版本中，您可以使用 **Debug > 重新附加至進程** ]，以重新附加至先前附加的相同進程 ... (Shift + Alt + P) 。

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

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 疑難排解在 Windows Server 上開啟必要的連接埠

在大部分的安裝中，ASP.NET 和遠端偵錯程式的安裝會開啟必要的埠。 但是，如果您要針對部署問題進行疑難排解，並將應用程式裝載于防火牆後方，您可能需要確認已開啟正確的埠。

在 Azure VM 上，您必須透過 [網路安全性群組](/azure/virtual-machines/windows/nsg-quickstart-portal)開啟埠。

必要的埠：

* 80-IIS 的必要元件
::: moniker range=">=vs-2019"
* 4024-從 Visual Studio 2019 進行遠端偵錯程式的必要 (如需詳細資訊，請參閱 [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)) 。
::: moniker-end
::: moniker range="vs-2017"
* 4022-從 Visual Studio 2017 進行遠端偵錯程式的必要 (如需詳細資訊，請參閱 [遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)) 。
::: moniker-end
* UDP 3702- (選擇性的) 探索埠可在您附加至 Visual Studio 中的遠端偵錯程式時，提供 [ **尋找** ] 按鈕。

此外，ASP.NET 安裝應已開啟這些埠：
- 8172- (Web Deploy 從 Visual Studio 部署應用程式所需的選擇性) 
