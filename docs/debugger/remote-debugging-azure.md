---
title: 遠端偵錯 IIS 與 Azure 上的 ASP.NET Core |Microsoft 文件
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: cc889accc116fb2115ae56155a190ed6ea2d3fc0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38797848"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>在 Visual Studio 2017 在 Azure 中的 IIS 上的遠端偵錯 ASP.NET Core

本指南說明如何安裝和設定 Visual Studio 2017 ASP.NET Core 應用程式、 將它部署到 IIS 使用 Azure，並附加從 Visual Studio 遠端偵錯工具。

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


### <a name="requirements"></a>需求

不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能失敗或非常慢。 需求的完整清單，請參閱 <<c0> [ 需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>在 Visual Studio 2017 電腦上建立 ASP.NET Core 應用程式 

1. 建立新的 ASP.NET Core 應用程式。 (選擇**檔案 > 新增 > 專案**，然後選取**Visual C# > 網路 > ASP.NET Core Web 應用程式**)。

    在**ASP.NET Core**範本區段中，選取**Web 應用程式**。

2. 請確定**ASP.NET Core 2.0**已選取，**啟用 Docker 支援**是**不**選取且**驗證**設為**不驗證**。

3. 將專案命名為**MyASPApp** ，按一下 **確定**建立新的方案。

4. 開啟 About.cshtml.cs 檔案，並中設定中斷點`OnGet`方法 (在較舊的範本中，開啟 HomeController.cs 改為和中設定中斷點`About()`方法)。

## <a name="remote_debug_azure_app_service"></a> Azure App Service 上的遠端偵錯 ASP.NET Core

從 Visual Studio 中，您可以快速發行及偵錯您的應用程式至 IIS 的完整佈建執行個體。 不過，在預設的 IIS 設定，而且您無法自訂它。 如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 (如果您需要自訂 IIS 功能，請嘗試偵錯[Azure VM](#remote_debug_azure_vm)。) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>若要部署應用程式，並使用伺服器總管 中的遠端偵錯

1. 在 Visual Studio 中，以滑鼠右鍵按一下專案節點，然後選擇**發佈**。

    如果您先前已設定任何發行的設定檔**發佈**窗格隨即出現。 按一下 **新的設定檔**。

1. 選擇**Azure App Service**從**發佈**對話方塊中，選取**新建**，並遵循提示來發行。

    如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

    ![發佈至 Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 開啟**伺服器總管**(**檢視** > **伺服器總管**)，以滑鼠右鍵按一下 App Service 執行個體，然後選擇 **附加偵錯工具**.

1. 執行的 ASP.NET 應用程式中，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。

    就這麼容易！ 本主題中步驟的其餘部分，適用於 Azure VM 上的遠端偵錯。

## <a name="remote_debug_azure_vm"></a> Azure VM 上的遠端偵錯 ASP.NET Core

您可以建立 Windows Server Azure VM，然後安裝並設定 IIS 和其他必要的軟體元件。 這花費的時間超出部署至 Azure App Service，而且需要您在本教學課程中遵循的其餘步驟。

首先，遵循所述的所有步驟[安裝和執行的 IIS](/azure/virtual-machines/windows/quick-create-portal)。

當您在網路安全性群組中開啟連接埠 80 時，也開啟連接埠 4022，遠端偵錯工具。 這樣一來，您就不必更新版本加以開啟。

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>已經執行 Azure VM 上的 在 IIS 中的應用程式嗎？

這篇文章包含的基本組態中的 Windows server 上的 IIS 設定和部署應用程式從 Visual Studio 中的步驟。 這些步驟都包含在內，以確定伺服器已安裝應用程式可以正確地執行，並在您已準備好遠端偵錯的必要的元件。

* 如果您的應用程式在 IIS 中執行，而且只想要下載遠端偵錯工具並開始偵錯，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您需要協助，請確定您的應用程式呈現設定而無法選取，部署，並在 IIS 中正確執行，以便您可以偵錯，請遵循本主題中的所有步驟。

### <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中 （它預設啟用），已啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，可讓您下載某些網頁伺服器元件。 新增信任的網站，方法是前往**網際網路選項 > 安全性 > 受信任的站台 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，您可能會收到負載各種 web 站台指令碼和資源的權限授與的要求。 其中一些資源並不需要，但若要簡化程序中，按一下**新增**出現提示時。

### <a name="install-aspnet-core-on-windows-server"></a>Windows 伺服器上安裝 ASP.NET Core

1. 安裝[.NET Core Windows Server 裝載](https://aka.ms/dotnetcore-2-windowshosting)主機系統上的套件組合。 組合將會安裝.NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 如需詳細的深入指示，請參閱[Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    > [!NOTE]
    > 如果系統沒有網際網路連線，取得並安裝 *[Microsoft Visual c + + 2015年可轉散發](https://www.microsoft.com/download/details.aspx?id=53840)* 之前安裝的.NET Core Windows Server 主控的組合。

3. 重新啟動系統 (或執行**net stop was /y**後面**net start w3svc**挑選系統 PATH 的變更在命令提示字元)。

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

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>匯入 Visual Studio 中的發佈設定和部署

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

在本教學課程中，我們會使用 Visual Studio 2017。

如果您無法開啟遠端偵錯工具下載頁面，請參閱[解除封鎖檔案下載](../debugger/remote-debugging.md#unblock_msvsmon)取得協助。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> 設定 Windows Server 上的遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增額外的使用者的權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。

### <a name="BKMK_attach"></a> 從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. Visual Studio 電腦上，開啟您嘗試偵錯方案 (**MyASPApp**如果您遵循這篇文章中的步驟)。
2. 在 Visual Studio 中，按一下**偵錯 > připojit k procesu** （Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017 中，您可以重新附加至您先前附加到使用相同的程序**偵錯 > 重新附加至處理序...**(Shift + Alt + P)。 

3. [限定詞] 欄位設定為**\<遠端電腦名稱 >: 4022**。
4. 按一下 **重新整理**。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您沒有看到任何處理程序，請嘗試使用的 IP 位址，而不 （連接埠是必要的） 遠端電腦名稱。 您可以使用`ipconfig`取得 IPv4 位址的命令列。

    如果您想要使用**尋找** 按鈕，您可能需要[開啟 UDP 連接埠 3702](#bkmk_openports)伺服器上。

5. 核取 [顯示所有使用者的處理序]  。

6. 輸入以快速找出處理序名稱的第一個字母*dotnet.exe* （適用於 ASP.NET Core)。
   
   ASP.NET Core 應用程式中，先前的程序名稱是*dnx.exe*。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. 按一下 [附加] 。

8. 開啟遠端電腦的網站。 在瀏覽器中，移至**http://\<遠端電腦名稱 >**。
    
    您應該會看到 ASP.NET 網頁。
9. 執行的 ASP.NET 應用程式中，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。

### <a name="bkmk_openports"></a> 疑難排解： 開啟 Windows Server 上的必要連接埠

在大部分的配置，所需的連接埠已開啟 ASP.NET 和遠端偵錯工具的安裝。 不過，如果您正在疑難排解部署問題的應用程式裝載在防火牆後方，您可能需要確認正確的連接埠已開啟。

在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic)。 

必要的連接埠：

- 80-所需的 IIS
- 4022-所需的 Visual Studio 2017 的遠端偵錯 (請參閱[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)如需詳細資訊)。
- UDP 3702-（選擇性） 探索連接埠即可**尋找**按鈕附加至 Visual Studio 中的遠端偵錯工具時。

此外，應該已經開啟這些連接埠，ASP.NET 安裝：
- 8172-（選擇性） 所需的 Web Deploy 來部署應用程式從 Visual Studio

