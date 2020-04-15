---
title: 遠端 iIS 計算機上的遠端調試ASP.NET核心 |微軟文件
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
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385470"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>遠端除錯ASP.NET視覺化演播室遠端 IIS 電腦上的核心

要調試已部署到 IIS 的 ASP.NET 核心應用程式,請在部署應用的電腦上安裝並運行遠端工具,然後從 Visual Studio 附加到正在運行的應用。

![遠端除錯器元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南介紹如何設置和配置 Visual Studio ASP.NET核心,將其部署到 IIS,以及從 Visual Studio 連接遠端調試器。 要ASP.NET 4.5.2 遠端除錯,請參閱[IIS 電腦上的遠端除錯ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 您還可以使用 Azure 在 IIS 上部署和調試。 對於 Azure 應用服務,可以使用[快照調試器](../debugger/debug-live-azure-applications.md)或[從伺服器資源管理器 附加調試器](../debugger/remote-debugging-azure.md),輕鬆在預配置的 IIS 實例和遠端除錯器上部署和調試。

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"
Visual Studio 2019 需要遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 需要遵循本文中所示的步驟。
::: moniker-end

這些過程已在以下伺服器設定上過測試:
* Windows 伺服器 2012 R2 和 IIS 8
* Windows 伺服器 2016 和 IIS 10

## <a name="network-requirements"></a>網路需求

不支援在通過代理連接的兩台計算機之間進行調試。 不建議通過高延遲或低頻寬連接(如撥號 Internet)或跨國家/地區的 Internet 進行調試,並且可能會失敗或速度過慢,令人無法接受。 有關需求的完整清單,請參閱[要求](../debugger/remote-debugging.md#requirements_msvsmon)。

## <a name="app-already-running-in-iis"></a>已在IIS中運行的應用?

本文包括有關在 Windows 伺服器上設置 IIS 的基本配置和從 Visual Studio 部署應用的步驟。 包括這些步驟,以確保伺服器已安裝所需的元件,應用可以正常運行,並且您已準備好進行遠端調試。

* 如果你的應用程式在 IIS 中執行,並且只想下載遠端除錯器並開始除錯,請轉到 Windows[伺服器下載並安裝遠端工具](#BKMK_msvsmon)。

* 如果希望幫助確保應用在IIS中設置、部署和正確運行,以便可以調試,請按照本主題中的所有步驟操作。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>在視覺化工作室電腦上建立ASP.NET核心應用程式

1. 建立新的 ASP.NET Core Web 應用程式。 

    ::: moniker range=">=vs-2019"
    從 Visual Studio 2019 中,鍵入**Ctrl + Q**以開啟搜尋框,鍵入**asp.net,** 選擇**樣本**,然後選擇**建立新ASP.NET核心 Web 應用程式**。 在顯示的對話框中,為專案**MyASApp**命名 ,然後選擇"**創建**"。 接下來,選擇**Web 應用程式(模型檢視控制器),** 然後選擇 **「創建**」 。。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從 Visual Studio 2017 中,選擇 **「檔案>新的>專案**」,然後選擇**Visual C# > Web >ASP.NET核心 Web 應用程式**。 在「ASP.NET核心樣本部份中,選擇**Web 應用程式(模型-檢視控制器)**。 請確保選擇了ASP.NET核心 2.1,未選擇**啟用 Docker 支援**,並且**身份驗證**設置為 **"無身份驗證**"。 命名專案**MyASApp**。
    ::: moniker-end

4. 打開About.cshtml.cs檔並在`OnGet`方法中設置斷點(在較舊的範本中,改為打開HomeController.cs`About()`並在 方法中設置斷點)。

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>在 Windows 伺服器上安裝及設定 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows 伺服器上的瀏覽器安全設定

如果在 Internet 資源管理器中啟用了增強的安全設定(預設情況下已啟用),則可能需要將某些域添加為受信任的網站,以便能夠下載某些 Web 伺服器元件。 通過訪問**互聯網選項>安全>受信任網站>網站**添加受信任的網站。 添加以下域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

下載軟體時,您可能會收到請求,請求授予載入各種網站腳本和資源的許可權。 其中一些資源不是必需的,但為了簡化該過程,請在提示時單擊 **「添加**」。。

## <a name="install-aspnet-core-on-windows-server"></a>在 Windows 伺服器上安裝 ASP.NET核心

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

1. 打開 Windows 資源管理器並創建新資料夾**C:\Publish,** 稍後將部署 ASP.NET 核心專案。

2. 如果尚未開啟,則開啟**網際網路資訊服務 (IIS) 管理員**。 (在伺服器管理員的左邊窗格中,選擇**IIS**。 以滑鼠右鍵按一下伺服器，然後選取 [Internet Information Services (IIS) 管理員]****。)

3. 在左邊窗格中的 **「連線」** 下,轉到 **「網站**」。

4. 選擇**預設網站**,選擇 **「基本設定**」,並將**實體路徑**設定為**C:\發布**。

4. 以滑鼠右鍵按一下 [預設的網站] **** 節點，並選取 [加入應用程式] ****。

5. 將**別名**字段設定為**MyASApp,** 接受預設應用程式池 (**預設 AppPool) ,** 並將**實體路徑**設定為**C:\發布**。

6. 在 **'連線'** 下,選擇**應用程式池**。 打開**預設應用程式池**並將應用程式池欄位設置為 **「無託管代碼**」。

7. 右鍵按一下 IIS 管理器中的新網站,選擇 **「編輯權限**」,並確保 IUSR、IIS_IUSRS 或設定為存取 Web 應用的使用者是具有讀取& 執行權限的授權使用者。

    如果您沒有看到這些使用者之一具有訪問許可權,請執行步驟,將IUSR添加為具有讀取&執行許可權的使用者。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>透過從視覺化工作室發布到本地資料夾來發佈和部署應用

您還可以使用檔案系統或其他工具發佈和部署應用。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>在 Windows 伺服器下載並安裝遠端工具

下載與您的 Visual Studio 版本相匹配的遠端工具版本。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>在 Windows 伺服器上設定遠端除錯器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果需要為其他使用者添加許可權,請更改身份驗證模式或遠端除錯器的連接埠號,請參閱[設定遠端除錯器](../debugger/remote-debugging.md#configure_msvsmon)。

有關將遠端除錯器作為服務執行的資訊,請參閱[將遠端除錯器作為服務執行](../debugger/remote-debugging.md#bkmk_configureService)。

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>從視覺化工作室電腦連接到ASP.NET應用程式

1. 在 Visual Studio 電腦上,打開您嘗試調試的解決方案(如果您正在按照本文中的所有步驟操作**MyASApp)。**
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

    * 如果您正在 IIS 上使用[應用內託管模型](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models),請選擇正確的**w3wp.exe**進程。 從 .NET 核心 3 開始,這是預設值。

    * 否則,選擇**dotnet.exe**進程。 (這是進程外託管模型。

    如果有多個進程顯示*w3wp.exe*或*dotnet.exe,* 請檢查**使用者名**列。 在某些情況下,「**使用者名**」列顯示應用池名稱,例如**IIS APPPOOL_預設AppPool。** 如果看到應用池,但它不唯一,請為要調試的應用實例創建新的名為 App Pool,然後您可以在 **「使用者名」** 列中輕鬆找到它。

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> 疑難排解在 Windows Server 上開啟必要的連接埠

在大多數設置中,通過安裝ASP.NET和遠端調試器打開所需的埠。 但是,您可能需要驗證埠是否處於打開狀態。

> [!NOTE]
> 在 Azure VM 上,必須透過[網路安全組](/azure/virtual-machines/windows/nsg-quickstart-portal)打開埠。

所需連接埠:

* 80 - IIS 需要
::: moniker range=">=vs-2019"
* 4024 - 從 Visual Studio 2019 進行遠端調試所需的(有關詳細資訊,請參閱[遠程調試器埠分配](../debugger/remote-debugger-port-assignments.md))。
::: moniker-end
::: moniker range="vs-2017"
* 4022 - 從 Visual Studio 2017 進行遠端調試所需的(有關詳細資訊,請參閱[遠程調試器埠分配](../debugger/remote-debugger-port-assignments.md))。
::: moniker-end
* UDP 3702 - (可選) 發現連接埠讓您能夠在連接到 Visual Studio 中的遠端除錯器時使用 **「尋找**」按鈕。

1. 要開啟 Windows 伺服器上的連接埠,開啟 **「開始」** 選單,搜尋**具有進階安全性**的 Windows 防火牆 。

2. 然後選擇 **「入站規則>>埠的新規則**,然後單擊」**下一步**」。。 ( 對於 UDP 3702,請選擇**出站規則**。

3. 在 **「特定本地埠**」下,輸入埠號,按下 **「下一步**」 。

4. 按下「**允許連接**」,按下 **「下一步**」。

5. 選擇要啟用埠的一個或多個網路類型,然後按下「**下一步**」。

    您選取的類型必須包括遠端電腦連線的網路。
6. 為入站規則添加名稱(例如 **,IIS、Web****部署**或**msvsmon),** 然後按一下 **"完成**"。

    您應該會在 [輸入規則] 或 [輸出規則] 清單中看到您的新規則。

    如果需要有關設定 Windows 防火牆的更多詳細資訊,請參閱[為遠端除錯設定 Windows 防火牆](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 為其他必需的埠創建其他規則。
