---
title: IIS 和 Azure 上的遠端調試ASP.NET核心 |微軟文件
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385500"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>遠端除錯ASP.NET視覺化工作室中 Azure 中的 IIS 核心

本指南介紹如何設置和配置 Visual Studio ASP.NET核心應用,使用 Azure 將其部署到 IIS,以及從 Visual Studio 附加遠端調試器。

建議在 Azure 上遠端除錯的方法取決於您的方案:

* 在 Azure 應用服務上執行試 ASP.NET核心,請參閱[使用快照除錯器 除錯 Azure 應用](../debugger/debug-live-azure-applications.md)。 這是建議的方法。
* 要使用更傳統的調試功能調試 Azure 應用服務上的 ASP.NET 核心,請按照本主題中的步驟操作(請參閱[Azure 應用服務上的"遠端調試](#remote_debug_azure_app_service)"部分)。

    在這種情況下,必須將應用從 Visual Studio 部署到 Azure,但無需手動安裝或配置 IIS 或遠端調試器(這些元件以虛線表示),如下圖所示。

    ![遠端除錯器元件](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* 要在 Azure VM 上調試 IIS,請按照本主題中的步驟操作(請參閱[Azure VM 上的"遠端調試"部分](#remote_debug_azure_vm))。 這允許您使用自定義的 IIS 配置,但設置和部署步驟更為複雜。

    對於 Azure VM,必須將應用從 Visual Studio 部署到 Azure,並且還需要手動安裝 IIS 角色和遠端調試器,如下圖所示。

    ![遠端除錯器元件](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* 要在 Azure 服務結構上調試ASP.NET核心,請參閱[除錯遠端服務結構應用程式](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)。

> [!WARNING]
> 請務必刪除完成本教程中的步驟後創建的 Azure 資源。 這樣,您就可以避免產生不必要的費用。

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"
Visual Studio 2019 需要遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 需要遵循本文中所示的步驟。
::: moniker-end

### <a name="network-requirements"></a>網路需求

不支援在通過代理連接的兩台計算機之間進行調試。 不建議通過高延遲或低頻寬連接(如撥號 Internet)或跨國家/地區的 Internet 進行調試,並且可能會失敗或速度過慢,令人無法接受。 有關需求的完整清單,請參閱[要求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>在視覺化工作室電腦上建立ASP.NET核心應用程式

1. 創建新ASP.NET核心應用程式。

    ::: moniker range=">=vs-2019"
    從 Visual Studio 2019 中,鍵入**Ctrl + Q**以開啟搜尋框,鍵入**asp.net,** 選擇**樣本**,然後選擇**建立新ASP.NET核心 Web 應用程式**。 在顯示的對話框中,為專案**MyASApp**命名 ,然後選擇"**創建**"。 接下來,選擇**Web 應用程式(模型檢視控制器),** 然後選擇 **「創建**」 。。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從 Visual Studio 2017 中,選擇 **「檔案>新的>專案**」,然後選擇**Visual C# > Web >ASP.NET核心 Web 應用程式**。 在「ASP.NET核心樣本部份中,選擇**Web 應用程式(模型-檢視控制器)**。 請確保選擇了ASP.NET核心 2.1,未選擇**啟用 Docker 支援**,並且**身份驗證**設置為 **"無身份驗證**"。 命名專案**MyASApp**。
    ::: moniker-end

1. 打開About.cshtml.cs檔並在`OnGet`方法中設置斷點(在較舊的範本中,改為打開HomeController.cs`About()`並在 方法中設置斷點)。

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Azure 應用服務上的遠端除錯ASP.NET核心

在 Visual Studio 中,您可以快速將應用發表到完全預配的 IIS 實體,並將應用調試到完全預配的 IIS 實例。 但是,IIS 的配置是預設的,您不能對其進行自定義。 有關更詳細的說明,請參閱使用[Visual Studio 將 ASP.NET 核心 Web 應用部署到 Azure。](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) (如果需要自定義 IIS 的能力,請嘗試在[Azure VM](#remote_debug_azure_vm)上進行調試。

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>使用雲端管理員部署應用程式與遠端除錯

1. 在可視化工作室中,右鍵單擊專案節點並選擇 **「發布**」。。

    如果您之前已設定任何發行設定檔，[發行]**** 窗格會隨即出現。 按下 **「新設定檔**」。

1. 從 **「發布」** 對話框中選擇**Azure 應用服務**,選擇 **「新建**」,然後按照提示創建設定檔。

    如需詳細指示，請參閱[使用 Visual Studio 將 ASP.NET Core Web 應用程式部署至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

    ![發佈到 Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 在"發佈"視窗中,選擇 **"編輯配置"** 並切換到調試配置,然後選擇 **「發布**」。

   調試應用需要調試配置。

1. 開放**雲資源管理員**(**查看** > **雲資源管理員**),右鍵按一下套用服務實體並選擇**額外除錯器**。

   如果雲資源管理員不可用,則改為打開伺服器資源管理員。 然後,右鍵按一下伺服器資源管理員中的應用服務實例,然後選擇**附加除錯器**。

1. 在正在運行的ASP.NET應用程式中,按一下指向 **「關於」** 頁面的連結。

    應該在 Visual Studio 中叫用中斷點。

    就這麼簡單！ 本主題中的其他步驟將應用於 Azure VM 上的遠端調試。

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Azure VM 上的遠端除錯ASP.NET核心

可以為 Windows 伺服器創建 Azure VM,然後安裝和配置 IIS 和其他必需的軟體元件。 這比部署到 Azure 應用服務所花費的時間要長,並且需要遵循本教程中的其餘步驟。

這些過程已在以下伺服器設定上過測試:
* Windows 伺服器 2012 R2 和 IIS 8
* Windows 伺服器 2016 和 IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>已在 Azure VM 上的 IIS 中運行的應用?

本文包括有關在 Windows 伺服器上設置 IIS 的基本配置和從 Visual Studio 部署應用的步驟。 包括這些步驟,以確保伺服器安裝了所需的元件,應用可以正常運行,並且您已準備好進行遠端調試。

* 如果你的應用程式在 IIS 中執行,並且只想下載遠端除錯器並開始除錯,請轉到 Windows[伺服器下載並安裝遠端工具](#BKMK_msvsmon)。

* 如果希望幫助確保應用在IIS中設置、部署和正確運行,以便可以調試,請按照本主題中的所有步驟操作。

  * 在開始之前,請按照安裝中描述的所有步驟[操作並執行 IIS](/azure/virtual-machines/windows/quick-create-portal)。

  * 在網路安全組開啟連接埠 80 時,還會開啟遠端除錯器 (4024 或 4022)[的正確連接埠](#bkmk_openports)。 這樣,您就不必稍後打開它了。

### <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows 伺服器上的瀏覽器安全設定

如果在 Internet 資源管理器中啟用了增強的安全設定(預設情況下已啟用),則可能需要將某些域添加為受信任的網站,以便能夠下載某些 Web 伺服器元件。 通過訪問**互聯網選項>安全>受信任網站>網站**添加受信任的網站。 添加以下域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

下載軟體時,您可能會收到請求,請求授予載入各種網站腳本和資源的許可權。 其中一些資源不是必需的,但為了簡化該過程,請在提示時單擊 **「添加**」。。

### <a name="install-aspnet-core-on-windows-server"></a>在 Windows 伺服器上安裝 ASP.NET核心

1. 在主控系統上安裝 [.NET Core Windows Server 裝載套件組合](https://aka.ms/dotnetcore-2-windowshosting)。 套件組合會安裝 .NET Core 執行階段、.NET Core 程式庫和 ASP.NET Core 模組。 有關更深入的說明,請參閱[發佈到 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

    > [!NOTE]
    > 如果系統沒有網路連線,請在安裝 .NET 核心 Windows 伺服器託管包之前取得並安裝*[Microsoft Visual C++ 2015 可再分發](https://www.microsoft.com/download/details.aspx?id=53840)*。

3. 重新啟動系統(或執行**凈停止為 /y,** 然後從命令提示符**淨啟動 w3svc**以選取對系統 PATH 的更改)。

## <a name="choose-a-deployment-option"></a>選擇部署選項

如果您需要將應用部署到 IIS 的説明,請考慮以下選項:

* 通過在IIS中創建發佈設定檔並在Visual Studio 中導入設置進行部署。 在某些情況下,這是部署應用的快速方法。 建立發佈設定檔時,許可權將自動在IIS中設置。

* 通過發佈到本地資料夾,並通過首選方法將輸出複製到IIS上準備好的應用資料夾進行部署。

## <a name="optional-deploy-using-a-publish-settings-file"></a>( 選擇性的 )使用設定設定檔進行部署

您可以使用此選項創建發佈設定檔並將其導入 Visual Studio。

> [!NOTE]
> 此部署方法使用 Web 部署。 如果要在 Visual Studio 中手動配置 Web 部署,而不是導入設置,則可以安裝 Web 部署 3.6,而不是為託管伺服器安裝 Web 部署 3.6。 但是,如果手動配置 Web 部署,則需要確保伺服器上的應用資料夾配置了正確的值和許可權(請參閱[配置 ASP.NET 網站](#BKMK_deploy_asp_net))。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>安裝與設定 Web 部署,用於在 Windows 伺服器上託管伺服器

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果應用不是從 Visual Studio 啟動的,則在 IIS 中啟動應用。 針對 ASP.NET Core，您必須先確定**DefaultAppPool** 的 [應用程式集區] 欄位設定為 [沒有受控程式碼]****。

1. 在 **「設定」** 對話方塊中,透過按**下 「下一步**」來啟用除錯,選擇 **「除錯**」設定,然後在 **「檔發佈**」選項下選擇 **「刪除目標的其他檔**」 。

    > [!NOTE]
    > 如果選擇「發佈」設定,則在發佈時禁用*Web.config*檔中的調試。

1. 按下 **"保存**",然後重新發佈應用。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>( 選擇性的 )透過本地端資料夾進行部署

如果要使用 PowerShell、RoboCopy 將應用複製到 IIS,或者想要手動複製檔,則可以使用此選項來部署應用。

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>在 Windows 伺服器電腦上設定ASP.NET核心網站

如果要導入發佈設置,可以跳過此部分。

1. 開啟 [Internet Information Services (IIS) 管理員] **** 並移至 [網站] ****。

2. 以滑鼠右鍵按一下 [預設的網站] **** 節點，並選取 [加入應用程式] ****。

3. 將**別名**字段設置為**MyASApp,** 將應用程式池欄位設置為 **「無託管代碼**」。 將**物理路徑**設置為**C:\發布**(稍後將部署ASP.NET核心專案)。

4. 在 IIS 管理員中選擇網站後,選擇 **「編輯權限**」,並確保為應用程式池配置的 IUSR、IIS_IUSRS 或使用者是具有讀取&執行權限的授權使用者。

    如果您沒有看到這些使用者之一具有訪問許可權,請執行步驟,將IUSR添加為具有讀取&執行許可權的使用者。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>( 選擇性的 )透過從視覺化工作室發布到本地資料夾來發佈和部署應用

如果不使用 Web 部署,則必須使用檔案系統或其他工具發布和部署應用。 您可以首先使用檔案系統創建包,然後手動部署包或使用其他工具(如 PowerShell、RoboCopy 或 XCopy)。 在本節中,我們假設您正在手動複製包,如果您不使用 Web 部署。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>在 Windows 伺服器下載並安裝遠端工具

下載與您的 Visual Studio 版本相匹配的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>在 Windows 伺服器上設定遠端除錯器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果需要為其他使用者添加許可權,請更改身份驗證模式或遠端除錯器的連接埠號,請參閱[設定遠端除錯器](../debugger/remote-debugging.md#configure_msvsmon)。

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>從視覺化工作室電腦連接到ASP.NET應用程式

1. 在 Visual Studio 電腦上,打開您嘗試調試的解決方案(如果您正在按照本文中的步驟操作,則**MyASApp)。**
2. 在可視化工作室中,單擊**調試>附加到進程**(Ctrl = Alt = P)。

    > [!TIP]
    > Visual Studio 2017 和更高版本中,您可以使用**除錯>重新附加到行程...**

3. 將「限定字段設定為**\<遠端電腦名稱>,** 然後按**Enter**。

    驗證 Visual Studio 是否將所需的連接埠加入到電腦名稱,該埠以格式顯示:**\<遠端電腦名稱>:連接埠**

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 上,您應該會看到**\<遠端電腦名稱>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 上,您應該會看到**\<遠端電腦名稱>:4022**
    ::: moniker-end
    埠是必需的。 如果看不到埠號,則手動添加它。

4. 按一下 [重新整理]****。
    您應該會看到有些處理程序會出現在 [可使用的處理序] **** 視窗。

    如果看不到任何進程,請嘗試使用 IP 位址而不是遠端電腦名稱(需要埠)。 您可以在`ipconfig`命令列中使用來取得 IPv4 位址。

    如果要使用 **「尋找」** 按鈕,可能需要在伺服器上[打開 UDP 連接埠 3702。](#bkmk_openports)

5. 核取 [顯示所有使用者的處理序]  ****。

6. 鍵入進程名稱的第一個字母以快速查找應用。

    * 選擇**dotnet.exe(** 對於 .NET 核心 )

      如果有多個行程顯示**dotnet.exe,** 請檢查**使用者名**列。 在某些情況下,「**使用者名**」列顯示應用池名稱,例如**IIS APPPOOL_預設AppPool。** 如果看到應用池,識別正確過程的一種簡單方法是為要調試的應用實例創建新的名為 App Pool,然後您可以在 **「使用者名」** 列中輕鬆找到它。

    * 在某些 IIS 專案中,您可能會在行程清單中找到應用程式名稱,例如**MyASPApp.exe**。 您可以附加到此過程。

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. 按一下 [附加] ****。

8. 開啟遠端電腦的網站。 在瀏覽器中，移至 **http://\<遠端電腦名稱>**。

    您應該會看到 ASP.NET 網頁。
9. 在正在運行的ASP.NET應用程式中,按一下指向 **「關於」** 頁面的連結。

    應該在 Visual Studio 中叫用中斷點。

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 疑難排解在 Windows Server 上開啟必要的連接埠

在大多數設置中,通過安裝ASP.NET和遠端調試器打開所需的埠。 但是,如果要解決部署問題,並且應用託管在防火牆後面,則可能需要驗證正確的埠是否打開。

在 Azure VM 上,必須透過[網路安全組](/azure/virtual-machines/windows/nsg-quickstart-portal)打開埠。

所需連接埠:

* 80 - IIS 需要
::: moniker range=">=vs-2019"
* 4024 - 從 Visual Studio 2019 進行遠端調試所需的(有關詳細資訊,請參閱[遠程調試器埠分配](../debugger/remote-debugger-port-assignments.md))。
::: moniker-end
::: moniker range="vs-2017"
* 4022 - 從 Visual Studio 2017 進行遠端調試所需的(有關詳細資訊,請參閱[遠程調試器埠分配](../debugger/remote-debugger-port-assignments.md))。
::: moniker-end
* UDP 3702 - (可選) 發現連接埠讓您能夠在連接到 Visual Studio 中的遠端除錯器時使用 **「尋找**」按鈕。

此外,這些埠應該已經通過ASP.NET安裝打開:
- 8172 - (可選)從視覺化工作室部署應用所需的 Web 部署
