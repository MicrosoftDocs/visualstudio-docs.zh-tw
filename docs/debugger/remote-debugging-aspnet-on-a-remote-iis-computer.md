---
title: 遠端 IIS 電腦上的遠端 Debug ASP.NET Core |Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f3741f9b510450dabfea5c1df4eec4b2e0868b26
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181156"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio 的遠端 IIS 電腦上的遠端 Debug ASP.NET Core

若要對已部署至 IIS 的 ASP.NET Core 應用程式進行偵測，請在您部署應用程式的電腦上安裝並執行遠端工具，然後從 Visual Studio 附加至您的執行中應用程式。

![遠端偵錯程式元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南說明如何安裝和設定 Visual Studio ASP.NET Core、將它部署到 IIS，以及從 Visual Studio 附加遠端偵錯程式。 若要進行遠端 debug ASP.NET 4.5.2，請參閱[IIS 電腦上的遠端偵錯程式 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 您也可以使用 Azure 在 IIS 上部署和調試。 對於 Azure App Service，您可以使用[快照偵錯工具](../debugger/debug-live-azure-applications.md)或[從伺服器總管附加調試](../debugger/remote-debugging-azure.md)程式，輕鬆地在預先設定的 IIS 和遠端偵錯程式實例上部署和偵測。

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

## <a name="network-requirements"></a>網路需求

不支援透過 proxy 連線的兩部電腦之間的調試。 不建議透過高延遲或低頻寬的連線（例如撥號網際網路，或透過網際網路跨國家/地區）進行調試，而且可能會失敗，或速度變慢。 如需完整的需求清單，請參閱[需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="app-already-running-in-iis"></a>應用程式已在 IIS 中執行？

本文包含在 Windows server 上設定 IIS 的基本設定，以及從 Visual Studio 部署應用程式的步驟。 其中包含這些步驟，以確保伺服器已安裝必要元件，應用程式可以正確執行，而且您已準備好進行遠端 debug。

* 如果您的應用程式是在 IIS 中執行，而您只想要下載遠端偵錯程式並開始進行偵測，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您想要協助確保您的應用程式在 IIS 中已正確設定、部署及執行，以便您可以進行 debug，請遵循本主題中的所有步驟。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上建立 ASP.NET Core 應用程式

1. 建立新的 ASP.NET Core Web 應用程式。 

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，鍵入**Ctrl + Q**開啟搜尋方塊，輸入**asp.net**，選擇 [**範本**]，然後選擇 [**建立新的 ASP.NET Core Web 應用程式**]。 在出現的對話方塊中，將專案命名為**MyASPApp**，然後選擇 [**建立**]。 接下來，選擇 [ **Web 應用程式（模型-視圖控制器）** ]，然後選擇 [**建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇 [檔案 **> 新增 > 專案**]，然後選取 [  **C# Visual > Web > ASP.NET Core Web 應用程式**]。 在 [ASP.NET Core 範本] 區段中，選取 [ **Web 應用程式（模型-視圖控制器）** ]。 請確定已選取 [ASP.NET Core 2.1]，但未選取 [**啟用 Docker 支援**]，而且該**驗證**設定為 [**不需要驗證**]。 將專案命名為**MyASPApp**。
    ::: moniker-end

4. 開啟 About.cshtml.cs 檔案，並在 `OnGet` 方法中設定中斷點（在較舊的範本中，改為開啟 HomeController.cs，然後在 `About()` 方法中設定中斷點）。

## <a name="bkmk_configureIIS"></a>在 Windows Server 上安裝和設定 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果已在 Internet Explorer 中啟用增強式安全性設定（預設為啟用），則您可能需要新增一些網域作為信任的網站，讓您能夠下載一些 web 伺服器元件。 前往 **網際網路選項 > 安全性 > 信任的網站 > 網站** 來新增信任的網站。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，您可能會收到要求，授與載入各種網站腳本和資源的許可權。 其中有些資源不是必要的，但若要簡化此程式，請在出現提示時按一下 [**新增**]。

## <a name="install-aspnet-core-on-windows-server"></a>在 Windows Server 上安裝 ASP.NET Core

1. 在主控系統上安裝 [.NET Core Windows Server 裝載套件組合](https://aka.ms/dotnetcore-2-windowshosting)。 套件組合會安裝 .NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 如需更深入的指示，請參閱[發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    > [!NOTE]
    > 如果系統沒有網際網路連線，請先取得並安裝 [Microsoft Visual C++ 2015 可轉散發套件](https://www.microsoft.com/download/details.aspx?id=53840)，再安裝 .NET Core Windows Server 裝載套件組合。

3. 重新啟動系統 (或從命令提示字元依序執行 **net stop was /y** 和 **net start w3svc**，讓系統 PATH 的變更生效)。

## <a name="choose-a-deployment-option"></a>選擇部署選項

如果您需要協助將應用程式部署至 IIS，請考慮下列選項：

* 藉由在 IIS 中建立發行設定檔案，並匯入 Visual Studio 中的設定來進行部署。 在某些情況下，這是部署應用程式的快速方式。 當您建立發行設定檔案時，會在 IIS 中自動設定許可權。

* 藉由發行至本機資料夾，然後將輸出以慣用方法複製到 IIS 上備妥的應用程式資料夾來進行部署。

## <a name="optional-deploy-using-a-publish-settings-file"></a>選擇性使用發行設定檔案部署

您可以使用此選項建立發行設定檔案，並將它匯入 Visual Studio。

> [!NOTE]
> 這個部署方法使用 Web Deploy。 如果您想要以手動方式在 Visual Studio 中設定 Web Deploy，而不是匯入設定，您可以安裝 Web Deploy 3.6，而不是 Web Deploy 3.6 來主控伺服器。 不過，如果您手動設定 Web Deploy，就必須確定伺服器上的應用程式資料夾已設定正確的值和許可權（請參閱[設定 ASP.NET 網站](#BKMK_deploy_asp_net)）。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>在 Windows Server 上安裝和設定主控伺服器的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果應用程式不是從 Visual Studio 啟動，請在 IIS 中啟動應用程式。 針對 ASP.NET Core，您必須先確定**DefaultAppPool** 的 [應用程式集區] 欄位設定為 [沒有受控程式碼]。

1. 在 [**設定**] 對話方塊中，按 **[下一步]** 以啟用偵錯工具，選擇 [ **Debug** ] 設定，然後選擇 [檔案**發行**選項] 底下的 [**移除目的地的其他**檔案]。

    > [!NOTE]
    > 如果您選擇發行設定，當您發行時，會停用*web.config*檔案中的調試。

1. 按一下 [**儲存**]，然後重新發佈應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>選擇性發行至本機資料夾以進行部署

如果您想要使用 PowerShell、RoboCopy 將應用程式複製到 IIS，或想要手動複製檔案，您可以使用此選項來部署您的應用程式。

### <a name="BKMK_deploy_asp_net"></a>在 Windows Server 電腦上設定 ASP.NET Core 網站

1. 開啟 Windows Explorer，並建立新的資料夾**C:\Publish**，稍後您將在其中部署 ASP.NET Core 專案。

2. 如果尚未開啟，請開啟 [ **Internet Information Services （IIS）管理員**]。 （在伺服器管理員的左窗格中，選取 [ **IIS**]。 以滑鼠右鍵按一下伺服器，然後選取 [Internet Information Services (IIS) 管理員]。)

3. 在左窗格的 [**連接**] 底下，移至 [**網站**]。

4. 選取 [**預設的網站**]，選擇 [**基本設定**]，然後將 [**實體路徑**] 設定為**C:\Publish**。

4. 以滑鼠右鍵按一下 [預設的網站] 節點，並選取 [加入應用程式]。

5. 將 [**別名**] 欄位設定為**MyASPApp**，接受預設應用程式集區（**DefaultAppPool**），並將**實體路徑**設定為**C:\Publish**。

6. 在 [**連接**] 底下，選取 [**應用程式**集區]。 開啟**DefaultAppPool** ，並將 [應用程式集區] 欄位設定為 [**沒有受控碼**]。

7. 以滑鼠右鍵按一下 [IIS 管理員] 中的新網站，選擇 [**編輯許可權**]，並確定 [IUSR]、[IIS_IUSRS] 或設定用來存取 web 應用程式的使用者是具有 [讀取 & 執行] 許可權的授權使用者。

    如果您看不到其中一個使用者的存取權，請執行將 IUSR 新增為具有讀取 & 執行許可權之使用者的步驟。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>藉由從 Visual Studio 發佈至本機資料夾來發佈和部署應用程式

您也可以使用檔案系統或其他工具來發行和部署應用程式。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>在 Windows Server 上下載並安裝遠端工具

下載與您的 Visual Studio 版本相符的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a>在 Windows Server 上設定遠端偵錯程式

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要為其他使用者新增許可權，請變更遠端偵錯程式的驗證模式或埠號碼，請參閱[設定遠端偵錯程式](../debugger/remote-debugging.md#configure_msvsmon)。

如需以服務方式執行遠端偵錯程式的詳細資訊，請參閱以[服務方式執行遠端偵錯程式](../debugger/remote-debugging.md#bkmk_configureService)。

## <a name="BKMK_attach"></a> 從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. 在 Visual Studio 電腦上，開啟您嘗試進行偵錯工具的解決方案（**MyASPApp** ，如果您遵循本文中的所有步驟）。
2. 在 Visual Studio 中，按一下  **Debug > 附加至進程** （Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017 和更新版本中，您可以使用**Debug > 重新附加至進程 ...** ，重新附加至您先前附加的相同進程 .。。（Shift + Alt + P）。

3. 將 辨識符號 欄位設定為 **\<遠端電腦名稱稱 >** 然後按**enter**。

    確認 Visual Studio 將所需的埠新增至電腦名稱稱，其格式會是： **\<遠端電腦名稱稱 >:p 埠 o**

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 上，您應該會看到 **\<的遠端電腦名稱稱 >： 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 上，您應該會看到 **\<的遠端電腦名稱稱 >： 4022**
    ::: moniker-end
    需要端口。 如果您沒有看到埠號碼，請以手動方式新增。

4. 按一下 [重新整理]。
    您應該會看到有些處理程序會出現在 [可使用的處理序] 視窗。

    如果您沒有看到任何進程，請嘗試使用 IP 位址，而不是遠端電腦名稱稱（需要端口）。 您可以在命令列中使用 `ipconfig` 來取得 IPv4 位址。

    如果您想要使用 [**尋找**] 按鈕，您可能需要在伺服器上[開啟 UDP 埠 3702](#bkmk_openports) 。

5. 核取 [顯示所有使用者的處理序]。

6. 輸入您的進程名稱的第一個字母，以快速找到您的應用程式。

    * 選取 [ **dotnet**]。

      如果您有多個進程顯示**dotnet**，請檢查 [**使用者名稱**] 資料行。 在某些情況下，[**使用者名稱**] 欄會顯示您的應用程式集區名稱，例如**IIS APPPOOL\DefaultAppPool**。 如果您看到應用程式集區，識別正確程式的簡單方法是針對您想要進行 debug 的應用程式實例建立新的命名應用程式集區，然後在 [**使用者名稱**] 資料行中輕鬆找到它。

    * 在某些 IIS 案例中，您可能會在進程清單中找到您的應用程式名稱，例如**MyASPApp。** 您可以改為附加至此進程。

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. 按一下 [附加]。

8. 開啟遠端電腦的網站。 在瀏覽器中，移至 **http://\<遠端電腦名稱>** 。

    您應該會看到 ASP.NET 網頁。

9. 在正在執行的 ASP.NET 應用程式中，按一下 [**關於**] 頁面的連結。

    應該在 Visual Studio 中叫用中斷點。

## <a name="bkmk_openports"></a>疑難排解在 Windows Server 上開啟必要的埠

在大部分的情況下，安裝 ASP.NET 和遠端偵錯程式會開啟所需的埠。 不過，您可能需要驗證埠是否已開啟。

> [!NOTE]
> 在 Azure VM 上，您必須透過[網路安全性群組](/azure/virtual-machines/windows/nsg-quickstart-portal)開啟埠。

必要的埠：

* 80-IIS 的必要
::: moniker range=">=vs-2019"
* 4024-從 Visual Studio 2019 進行遠端偵錯的必要作業（如需詳細資訊，請參閱[遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)）。
::: moniker-end
::: moniker range="vs-2017"
* 4022-從 Visual Studio 2017 進行遠端偵錯的必要作業（如需詳細資訊，請參閱[遠端偵錯程式埠指派](../debugger/remote-debugger-port-assignments.md)）。
::: moniker-end
* UDP 3702-（選擇性）探索埠可讓您在 Visual Studio 中附加至遠端偵錯程式時，**找到 [尋找**] 按鈕。

1. 若要在 Windows Server 上開啟埠，請開啟 [**開始**] 功能表，搜尋 [**具有 Advanced Security 的 Windows 防火牆**]。

2. 然後選擇 **輸入規則 > 新規則 > 埠**，然後按**下一步**。 （如果是 UDP 3702，請選擇 [**輸出規則**]）。

3. 在 [**特定本機埠**] 底下，輸入埠號碼，然後按 **[下一步]** 。

4. 按一下 [**允許連接**]，然後按 **[下一步]** 。

5. 選取要為埠啟用的一或多個網路類型，然後按 **[下一步]** 。

    您選取的類型必須包括遠端電腦連線的網路。
6. 新增輸入規則的名稱（例如**IIS**、 **Web Deploy**或**Msvsmon**），然後按一下 **[完成]** 。

    您應該會在 [輸入規則] 或 [輸出規則] 清單中看到您的新規則。

    如果您想要更多有關設定 Windows 防火牆的詳細資訊，請參閱[設定 Windows 防火牆以進行遠端偵錯程式](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 為其他必要的埠建立其他規則。
