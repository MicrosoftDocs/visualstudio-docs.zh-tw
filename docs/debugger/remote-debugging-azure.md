---
title: 遠端偵錯 IIS 與 Azure 上的 ASP.NET Core |Microsoft 文件
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: afed42cbdb03ba0fb47880ed0126bad9858f83fa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040699"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>在 Visual Studio 中的 Azure 中的 IIS 上的遠端偵錯 ASP.NET Core

本指南說明如何安裝和設定 Visual Studio ASP.NET Core 應用程式、 將它部署到 IIS 使用 Azure，並附加遠端偵錯工具從 Visual Studio。

在 Azure 上的遠端偵錯的建議的方式取決於您的案例：

* 若要偵錯 ASP.NET Core Azure App Service 上，請參閱[使用快照集偵錯工具的偵錯 Azure 應用程式](../debugger/debug-live-azure-applications.md)。 這是建議的方法。
* 若要偵錯 ASP.NET Core 上使用較傳統的偵錯功能的 Azure 應用程式服務，請遵循本主題中的步驟 (請參閱節[遠端偵錯 Azure App Service 上](#remote_debug_azure_app_service))。

    在此案例中，您必須部署至 Azure 應用程式從 Visual Studio，但您不需要手動安裝或設定 IIS 或遠端偵錯工具 （這些元件會以虛線表示），如下圖所示。

    ![遠端偵錯工具元件](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* 若要偵錯在 Azure VM 上的 IIS，請遵循本主題中的步驟 (請參見[在 Azure VM 上的遠端偵錯](#remote_debug_azure_vm))。 這可讓您使用自訂的 IIS 設定，但更複雜的安裝和部署步驟。

    為 Azure 虛擬機器中，您必須部署至 Azure 應用程式從 Visual Studio，您也需要手動安裝 IIS 角色和遠端偵錯工具中，如下圖所示。

    ![遠端偵錯工具元件](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* 若要偵錯在 Azure Service Fabric ASP.NET Core 時，請參閱[遠端 Service Fabric 應用程式進行偵錯](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)。

> [!WARNING]
> 請務必刪除您已完成的步驟，在本教學課程時所建立的 Azure 資源。 這樣一來，您可以避免產生不必要的費用。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"
Visual Studio 2019，才能遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017，才能遵循本文中所示的步驟。
::: moniker-end

### <a name="network-requirements"></a>網路需求

不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能失敗或非常慢。 需求的完整清單，請參閱 <<c0> [ 需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio 電腦上建立 ASP.NET Core 應用程式

1. 建立新的 ASP.NET Core 應用程式。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019，輸入**Ctrl + Q**來開啟 搜尋 方塊中，輸入**asp.net**，選擇 **範本**，然後選擇 **建立新的 ASP.NET Core Web 應用程式**. 在出現的對話方塊中，為專案名稱**MyASPApp**，然後選擇**建立**。 接下來，選擇**Web 應用程式 （模型-檢視-控制器）**，然後選擇**建立**。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇**檔案 > 新增 > 專案**，然後選取**視覺化C#> Web > ASP.NET Core Web 應用程式**。 在 [ASP.NET Core 範本] 區段中，選取**Web 應用程式 （模型-檢視-控制器）**。 請確定選取 ASP.NET Core 2.1，，**啟用 Docker 支援**未選取且**驗證**設定為**不需要驗證**。 將專案命名為**MyASPApp**。
    ::: moniker-end

1. 開啟 About.cshtml.cs 檔案，並中設定中斷點`OnGet`方法 (在較舊的範本中，開啟 HomeController.cs 改為和中設定中斷點`About()`方法)。

## <a name="remote_debug_azure_app_service"></a> Azure App Service 上的遠端偵錯 ASP.NET Core

從 Visual Studio 中，您可以快速發行及偵錯您的應用程式至 IIS 的完整佈建執行個體。 不過，在預設的 IIS 設定，而且您無法自訂它。 如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 (如果您需要自訂 IIS 功能，請嘗試偵錯[Azure VM](#remote_debug_azure_vm)。)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>若要部署應用程式，並使用伺服器總管 中的遠端偵錯

1. 在 Visual Studio 中，以滑鼠右鍵按一下專案節點，然後選擇**發佈**。

    如果您之前已設定任何發行設定檔，[發行] 窗格會隨即出現。 按一下 **新的設定檔**。

1. 選擇**Azure App Service**從**發佈**對話方塊中，選取**新建**，並遵循提示來發行。

    如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

    ![發佈至 Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 開啟**伺服器總管**(**檢視** > **伺服器總管**)，以滑鼠右鍵按一下 App Service 執行個體，然後選擇 **附加偵錯工具**.

1. 執行的 ASP.NET 應用程式中，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。

    就這麼容易！ 本主題中步驟的其餘部分，適用於 Azure VM 上的遠端偵錯。

## <a name="remote_debug_azure_vm"></a> Azure VM 上的遠端偵錯 ASP.NET Core

您可以建立 Windows Server Azure VM，然後安裝並設定 IIS 和其他必要的軟體元件。 這花費的時間超出部署至 Azure App Service，而且需要您在本教學課程中遵循的其餘步驟。

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 8
* Windows Server 2016 和 IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>已經執行 Azure VM 上的 在 IIS 中的應用程式嗎？

這篇文章包含的基本組態中的 Windows server 上的 IIS 設定和部署應用程式從 Visual Studio 中的步驟。 這些步驟都包含在內，以確定伺服器已安裝應用程式可以正確地執行，並在您已準備好遠端偵錯的必要的元件。

* 如果您的應用程式在 IIS 中執行，而且只想要下載遠端偵錯工具並開始偵錯，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您需要協助，請確定您的應用程式呈現設定而無法選取，部署，並在 IIS 中正確執行，以便您可以偵錯，請遵循本主題中的所有步驟。

    * 在開始之前，請依照下列所述的所有步驟[安裝和執行的 IIS](/azure/virtual-machines/windows/quick-create-portal)。

    * 當您在網路安全性群組中開啟連接埠 80 時，也開啟[更正連接埠](#bkmk_openports)遠端偵錯工具 （4024 或 4022）。 這樣一來，您就不必更新版本加以開啟。

### <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中 （它預設啟用），已啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，可讓您下載某些網頁伺服器元件。 新增信任的網站，方法是前往**網際網路選項 > 安全性 > 受信任的站台 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，您可能會收到負載各種 web 站台指令碼和資源的權限授與的要求。 其中一些資源並不需要，但若要簡化程序中，按一下**新增**出現提示時。

### <a name="install-aspnet-core-on-windows-server"></a>Windows 伺服器上安裝 ASP.NET Core

1. 在主控系統上安裝 [.NET Core Windows Server 裝載套件組合](https://aka.ms/dotnetcore-2-windowshosting)。 組合將會安裝.NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 如需詳細的深入指示，請參閱[Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    > [!NOTE]
    > 如果系統沒有網際網路連線，請先取得並安裝 [Microsoft Visual C++ 2015 可轉散發套件](https://www.microsoft.com/download/details.aspx?id=53840)，再安裝 .NET Core Windows Server 裝載套件組合。

3. 重新啟動系統 (或從命令提示字元依序執行 **net stop was /y** 和 **net start w3svc**，讓系統 PATH 的變更生效)。

## <a name="choose-a-deployment-option"></a>選擇部署選項

如果您需要協助以部署至 IIS 的應用程式，請考慮這些選項：

* 在 IIS 中建立的發行設定檔和匯入 Visual Studio 中的設定來部署。 在某些情況下，這是可快速部署您的應用程式。 當您建立發行設定檔時，權限會自動設定 IIS 中。

* 部署發行至本機資料夾，並將輸出複製所慣用的方法，在 IIS 上備妥的應用程式資料夾。

## <a name="optional-deploy-using-a-publish-settings-file"></a>（選擇性）部署使用的發行設定檔

您可以使用此選項建立的發行設定檔，然後匯入 Visual Studio。

> [!NOTE]
> 這種部署方法會使用 Web Deploy。 如果您想要設定 Web Deploy 以手動方式在 Visual Studio 中而不是匯入設定，您可以安裝而不是 Web 部署 3.6 Web 部署 3.6 的主控伺服器。 不過，如果您設定 Web Deploy 以手動方式，您必須確定伺服器上的應用程式 資料夾已使用正確的值和權限 (請參閱[設定 ASP.NET 網站](#BKMK_deploy_asp_net))。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>安裝和設定 Windows Server 上的主控伺服器的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果應用程式從 Visual Studio 不會啟動，請在 IIS 中啟動應用程式。 您需要確定應用程式集區欄位的 ASP.NET Core **DefaultAppPool**設**沒有 Managed 程式碼**。

1. 在**設定**對話方塊中，按一下 偵錯的啟用**下一步**，選擇**偵錯**組態，然後選擇 **移除其他檔案目的地**底下**檔案發行**選項。

    > [!NOTE]
    > 如果您選擇發行組態時，您停用中的偵錯*web.config*檔案在發行時。

1. 按一下 **儲存**然後重新發行應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>（選擇性）部署發行至本機資料夾

您可以使用此選項來部署您的應用程式，如果您想要將應用程式複製到 IIS 使用 Powershell、 RoboCopy，或是您想要以手動方式將檔案複製。

### <a name="BKMK_deploy_asp_net"></a> 設定 Windows Server 電腦上的 ASP.NET 網站

如果您要匯入發佈設定，您可以略過本節。

1. 開啟 [Internet Information Services (IIS) 管理員]  並移至 [網站] 。

2. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

3. 設定**別名**欄位設為**MyASPApp** ，讓應用程式集區欄位**沒有 Managed 程式碼**。 設定**實體路徑**要**C:\Publish** （其中您稍後將部署的 ASP.NET 專案）。

4. 在 IIS 管理員中選取站台後，選擇**編輯權限**，並確定該 IUSR、 IIS_IUSRS 或 設定應用程式集區是授權的使用者具有讀取與執行權限的使用者。

    如果您沒有看到其中一個使用者具有存取權，經歷具有讀取與執行權限的使用者身分新增 IUSR 的步驟。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>（選擇性）發佈和部署應用程式發行至本機資料夾從 Visual Studio

如果您不使用 Web Deploy，您必須發佈和部署應用程式使用檔案系統或其他工具。 您可以開始使用檔案系統中，建立封裝，然後以手動方式部署封裝或使用其他工具，像是 PowerShell、 RoboCopy 或 XCopy。 在本節中，我們假設您以手動方式複製的套件，如果您不使用 Web Deploy。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> 下載並安裝 Windows Server 上的遠端工具

下載符合您的 Visual Studio 版本的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> 設定 Windows Server 上的遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增額外的使用者的權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。

### <a name="BKMK_attach"></a> 從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. Visual Studio 電腦上，開啟您嘗試偵錯方案 (**MyASPApp**如果您遵循這篇文章中的步驟)。
2. 在 Visual Studio 中，按一下**偵錯 > připojit k procesu** （Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017 和更新版本中，您可以重新附加至您先前附加到使用相同的程序**偵錯 > 重新附加至處理序...**(Shift + Alt + P)。

3. [限定詞] 欄位設定為**\<遠端電腦名稱 >** 按下**Enter**。

    確認，Visual Studio 會將所需的連接埠新增至 電腦名稱，就會出現在格式： **\<遠端電腦名稱 >： 連接埠**

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019，您應該會看到**\<遠端電腦名稱 >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017，您應該會看到**\<遠端電腦名稱 >: 4022**
    ::: moniker-end
    需要連接埠。 如果您沒有看到連接埠號碼，請手動新增。

4. 按一下 [重新整理]。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您沒有看到任何處理程序，請嘗試使用的 IP 位址，而不 （連接埠是必要的） 遠端電腦名稱。 您可以使用`ipconfig`取得 IPv4 位址的命令列。

    如果您想要使用**尋找** 按鈕，您可能需要[開啟 UDP 連接埠 3702](#bkmk_openports)伺服器上。

5. 核取 [顯示所有使用者的處理序]  。

6. 輸入您的處理程序名稱，以快速找出您的應用程式的第一個字母。

    * 選取  **dotnet.exe** （適用於.NET Core)

      如果您有多個處理序顯示**dotnet.exe**，檢查**使用者名**資料行。 在某些情況下，**使用者名**資料行中顯示您應用程式集區的名稱，例如**IIS APPPOOL\DefaultAppPool**。 如果您會看到應用程式集區，輕鬆地找出正確的處理序是建立新應用程式集區命名為應用程式執行個體，您要偵錯，然後您可以找到它輕鬆地在**使用者名**資料行。

    * 在某些 IIS 案例中，您可能會發現您的應用程式名稱在程序清單中，這類**MyASPApp.exe**。 您可以改為附加至此處理序。

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. 按一下 [附加] 。

8. 開啟遠端電腦的網站。 在瀏覽器中，移至 **http://\<遠端電腦名稱>**。

    您應該會看到 ASP.NET 網頁。
9. 執行的 ASP.NET 應用程式中，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。

### <a name="bkmk_openports"></a> 疑難排解：在 Windows Server 上開啟必要的連接埠

在大部分的配置，所需的連接埠已開啟 ASP.NET 和遠端偵錯工具的安裝。 不過，如果您正在疑難排解部署問題的應用程式裝載在防火牆後方，您可能需要確認正確的連接埠已開啟。

在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/windows/nsg-quickstart-portal)。

必要的連接埠：

* 80-所需的 IIS
::: moniker range=">=vs-2019"
* 4024-所需的 Visual Studio 2019 的遠端偵錯 (請參閱[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)如需詳細資訊)。
::: moniker-end
::: moniker range="vs-2017"
* 4022-所需的 Visual Studio 2017 的遠端偵錯 (請參閱[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)如需詳細資訊)。
::: moniker-end
* UDP 3702-（選擇性） 探索連接埠即可**尋找**按鈕附加至 Visual Studio 中的遠端偵錯工具時。

此外，應該已經開啟這些連接埠，ASP.NET 安裝：
- 8172-（選擇性） 所需的 Web Deploy 來部署應用程式從 Visual Studio
