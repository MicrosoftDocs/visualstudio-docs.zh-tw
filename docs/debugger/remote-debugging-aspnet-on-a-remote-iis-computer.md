---
title: 遠端偵錯 IIS 的遠端電腦上的 ASP.NET Core |Microsoft Docs
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
ms.openlocfilehash: 9d92ebc40fb61be5ddb6125799c07eee3d148551
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355496"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>在 Visual Studio 中的遠端執行 IIS 的電腦上的遠端偵錯 ASP.NET Core
偵錯已部署至 IIS 的 ASP.NET 應用程式，安裝並部署您的應用程式的所在的電腦上執行遠端工具，然後連結至您執行的應用程式從 Visual Studio。

![遠端偵錯工具元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南說明如何安裝和設定 Visual Studio 的 ASP.NET Core、 將它部署至 IIS，並從 Visual Studio 附加遠端偵錯工具。 若要遠端偵錯 ASP.NET 4.5.2，請參閱[在 IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 您也可以部署，並使用 Azure 的 IIS 上進行偵錯。 針對 Azure App Service，您可以輕鬆地部署和偵錯 IIS 和遠端偵錯工具，並使用預先設定的執行個體上[快照集偵錯工具](../debugger/debug-live-azure-applications.md)或是[從 伺服器總管附加偵錯工具](../debugger/remote-debugging-azure.md)。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"
Visual Studio 2019，才能遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017，才能遵循本文中所示的步驟。
::: moniker-end

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 8
* Windows Server 2016 和 IIS 10

## <a name="network-requirements"></a>網路需求

不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能失敗或非常慢。 需求的完整清單，請參閱 <<c0> [ 需求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="app-already-running-in-iis"></a>已在 IIS 中執行的應用程式嗎？

這篇文章包含的基本組態中的 Windows server 上的 IIS 設定和部署應用程式從 Visual Studio 中的步驟。 這些步驟都包含在內，以確定伺服器具有所需的安裝應用程式可以正確地執行，並在您已準備好遠端偵錯的元件。

* 如果您的應用程式在 IIS 中執行，而且只想要下載遠端偵錯工具並開始偵錯，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您需要協助，請確定您的應用程式呈現設定而無法選取，部署，並在 IIS 中正確執行，以便您可以偵錯，請遵循本主題中的所有步驟。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio 電腦上建立 ASP.NET Core 應用程式

1. 建立新的 ASP.NET Core Web 應用程式。 

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019，輸入**Ctrl + Q**來開啟 搜尋 方塊中，輸入**asp.net**，選擇 **範本**，然後選擇 **建立新的 ASP.NET Core Web 應用程式**. 在出現的對話方塊中，為專案名稱**MyASPApp**，然後選擇**建立**。 接下來，選擇**Web 應用程式 （模型-檢視-控制器）**，然後選擇**建立**。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇**檔案 > 新增 > 專案**，然後選取**視覺化C#> Web > ASP.NET Core Web 應用程式**。 在 [ASP.NET Core 範本] 區段中，選取**Web 應用程式 （模型-檢視-控制器）**。 請確定選取 ASP.NET Core 2.1，，**啟用 Docker 支援**未選取且**驗證**設定為**不需要驗證**。 將專案命名為**MyASPApp**。
    ::: moniker-end

4. 開啟 About.cshtml.cs 檔案，並中設定中斷點`OnGet`方法 (在較舊的範本中，開啟 HomeController.cs 改為和中設定中斷點`About()`方法)。

## <a name="bkmk_configureIIS"></a> 安裝及設定 Windows Server 上的 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中 （它預設啟用），已啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，可讓您下載某些網頁伺服器元件。 新增信任的網站，方法是前往**網際網路選項 > 安全性 > 受信任的站台 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，您可能會收到負載各種 web 站台指令碼和資源的權限授與的要求。 其中一些資源並不需要，但若要簡化程序中，按一下**新增**出現提示時。

## <a name="install-aspnet-core-on-windows-server"></a>在 Windows Server 上安裝 ASP.NET Core

1. 在主控系統上安裝 [.NET Core Windows Server 裝載套件組合](https://aka.ms/dotnetcore-2-windowshosting)。 套件組合會安裝 .NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 如需詳細的深入指示，請參閱[Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

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

應用程式部署成功之後，它應該會自動啟動。 如果應用程式從 Visual Studio 不會啟動，請在 IIS 中啟動應用程式。 針對 ASP.NET Core，您必須先確定**DefaultAppPool** 的 [應用程式集區] 欄位設定為 [沒有受控程式碼]。

1. 在**設定**對話方塊中，按一下 偵錯的啟用**下一步**，選擇**偵錯**組態，然後選擇 **移除其他檔案目的地**底下**檔案發行**選項。

    > [!NOTE]
    > 如果您選擇發行組態時，您停用中的偵錯*web.config*檔案在發行時。

1. 按一下 **儲存**然後重新發行應用程式。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>（選擇性）部署發行至本機資料夾

您可以使用此選項來部署您的應用程式，如果您想要將應用程式複製到 IIS 使用 Powershell、 RoboCopy，或是您想要以手動方式將檔案複製。

### <a name="BKMK_deploy_asp_net"></a> 設定 Windows Server 電腦上的 ASP.NET 網站

1. 開啟 Windows 檔案總管，並建立新的資料夾中， **C:\Publish**將稍後部署 ASP.NET 專案。

2. 如果它尚未開啟，開啟**Internet Information Services (IIS) 管理員**。 (在左窗格的 伺服器管理員中，選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取 [Internet Information Services (IIS) 管理員]。)

3. 底下**連線**在左窗格中，移至**站台**。

4. 選取  **Default Web Site**，選擇**基本設定**，並將**實體路徑**至**C:\Publish**。

4. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

5. 設定**別名**欄位設為**MyASPApp**，接受預設的應用程式集區 (**DefaultAppPool**)，並將**實體路徑**至**C:\Publish**。

6. 底下**連線**，選取**應用程式集區**。 開啟**DefaultAppPool**和應用程式集區欄位設為**沒有 Managed 程式碼**。

7. 以滑鼠右鍵按一下新的網站在 IIS 管理員中，選擇**編輯權限**，並確定該 IUSR、 IIS_IUSRS 或 設定 web 應用程式的存取是授權的使用者具有讀取與執行權限的使用者。

    如果您沒有看到其中一個使用者具有存取權，經歷具有讀取與執行權限的使用者身分新增 IUSR 的步驟。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>發佈和部署應用程式發行至本機資料夾從 Visual Studio

您可以發佈和部署應用程式使用檔案系統或其他工具。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> 下載並安裝 Windows Server 上的遠端工具

下載符合您的 Visual Studio 版本的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> 設定 Windows Server 上的遠端偵錯工具

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果您需要新增額外的使用者的權限變更驗證模式或遠端偵錯工具連接埠號碼，請參閱[設定遠端偵錯工具](../debugger/remote-debugging.md#configure_msvsmon)。

如需以服務方式執行遠端偵錯工具資訊，請參閱[以服務方式執行遠端偵錯工具](../debugger/remote-debugging.md#bkmk_configureService)。

## <a name="BKMK_attach"></a> 從 Visual Studio 電腦連接至 ASP.NET 應用程式

1. Visual Studio 電腦上，開啟您嘗試偵錯方案 (**MyASPApp**您是否已遵循這篇文章中的所有步驟)。
2. 在 Visual Studio 中，按一下**偵錯 > připojit k procesu** （Ctrl + Alt + P）。

    > [!TIP]
    > 在 Visual Studio 2017 和更新版本中，您可以重新附加至您先前附加到使用相同的程序**偵錯 > 重新附加至處理序...**（shift + Alt + P）。

3. [限定詞] 欄位設定為**\<遠端電腦名稱 >： 連接埠**。

    ::: moniker range=">=vs-2019"
    **\<遠端電腦名稱 >: 4024**於 Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **\<遠端電腦名稱 >: 4022**上 Visual Studio 2017
    ::: moniker-end
4. 按一下 [重新整理]。
    您應該會看到有些處理程序會出現在 [可使用的處理序]  視窗。

    如果您沒有看到任何處理程序，請嘗試使用的 IP 位址，而不 （連接埠是必要的） 遠端電腦名稱。 您可以使用`ipconfig`取得 IPv4 位址的命令列。

    如果您想要使用**尋找** 按鈕，您可能需要[開啟 UDP 連接埠 3702](#bkmk_openports)伺服器上。

5. 核取 [顯示所有使用者的處理序]  。
6. 輸入以快速找出處理序名稱的第一個字母**dotnet.exe** （適用於 ASP.NET Core)。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. 按一下 [附加] 。

8. 開啟遠端電腦的網站。 在瀏覽器中，移至 **http://\<遠端電腦名稱>**。

    您應該會看到 ASP.NET 網頁。

9. 執行的 ASP.NET 應用程式中，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。

## <a name="bkmk_openports"></a> 疑難排解在 Windows Server 上開啟必要的連接埠

在大部分的配置，所需的連接埠已開啟 ASP.NET 和遠端偵錯工具的安裝。 不過，您可能需要確認已開啟連接埠。

> [!NOTE]
> 在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/windows/nsg-quickstart-portal)。

必要的連接埠：

* 80-所需的 IIS
::: moniker range=">=vs-2019"
* 4024-所需的 Visual Studio 2019 的遠端偵錯 (請參閱[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)如需詳細資訊)。
::: moniker-end
::: moniker range="vs-2017"
* 4022-所需的 Visual Studio 2017 的遠端偵錯 (請參閱[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)如需詳細資訊)。
::: moniker-end
* UDP 3702-（選擇性） 探索連接埠即可**尋找**按鈕附加至 Visual Studio 中的遠端偵錯工具時。

1. 若要開啟 Windows Server 上的連接埠，請開啟**開始**功能表中，搜尋**具有進階安全性的 Windows 防火牆**。

2. 然後選擇**輸入規則 > 新的規則 > 連接埠**，然後按一下**下一步**。 (針對 UDP 3702 選擇**輸出規則**改用。)

3. 底下**特定本機連接埠**，輸入連接埠號碼，按一下**下一步**。

4. 按一下 [**允許連線**，按一下**下一步]**。

5. 選取一或多個網路類型，以啟用連接埠，並按一下**下一步**。

    您選取的類型必須包括遠端電腦連線的網路。
6. 新增名稱 (例如**IIS**， **Web Deploy**，或**msvsmon**) 的輸入規則，然後按一下 **完成**。

    您應該會在 [輸入規則] 或 [輸出規則] 清單中看到您的新規則。

    如果您想在 Windows 防火牆設定的更多詳細資料，請參閱[設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 建立其他必要的連接埠的其他規則。
