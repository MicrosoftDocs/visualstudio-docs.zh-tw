---
title: 在 IIS 電腦上對 ASP.NET 進行遠端偵錯
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: ba255d1d1e906e8fe7bacd05d1f4afd4b7bf413b
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366467"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>在執行 IIS 的遠端電腦上對 ASP.NET 進行遠端偵錯
偵錯已部署至 IIS 的 ASP.NET 應用程式，安裝並部署您的應用程式的所在的電腦上執行遠端工具，然後連結至您執行的應用程式從 Visual Studio。

![遠端偵錯工具元件](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

本指南說明如何安裝和設定 Visual Studio ASP.NET MVC 4.5.2 應用程式、 將它部署至 IIS，並從 Visual Studio 附加遠端偵錯工具。

> [!NOTE]
> 若要遠端改為偵錯 ASP.NET Core，請參閱[遠端偵錯 ASP.NET Core 在 IIS 電腦上](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。 針對 Azure App Service，您可以輕鬆地部署和偵錯的 IIS 使用的預先設定的執行個體上[快照集偵錯工具](../debugger/debug-live-azure-applications.md)(.NET 4.6.1 所需) 或由[從 伺服器總管附加偵錯工具](../debugger/remote-debugging-azure.md)。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"
Visual Studio 2019，才能遵循本文中所示的步驟。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017，才能遵循本文中所示的步驟。
::: moniker-end

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 8 （Windows Server 2008 R2，伺服器的步驟並不等於）

## <a name="network-requirements"></a>網路需求

從 Windows Server 2008 Service Pack 2 的 Windows Server 支援遠端偵錯工具。 需求的完整清單，請參閱 <<c0> [ 需求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支援透過 proxy 連線的兩部電腦之間的偵錯。 透過高延遲或低頻寬連線，例如撥號網際網路，或透過網際網路偵錯跨國家/地區不建議使用和可能失敗或非常慢。

## <a name="app-already-running-in-iis"></a>已在 IIS 中執行的應用程式嗎？

這篇文章包含的基本組態中的 Windows server 上的 IIS 設定和部署應用程式從 Visual Studio 中的步驟。 這些步驟都包含在內，以確定伺服器具有所需的安裝應用程式可以正確地執行，並在您已準備好遠端偵錯的元件。

* 如果您的應用程式在 IIS 中執行，而且只想要下載遠端偵錯工具並開始偵錯，請移至[下載並安裝 Windows Server 上的遠端工具](#BKMK_msvsmon)。

* 如果您需要協助，請確定您的應用程式呈現設定而無法選取，部署，並在 IIS 中正確執行，以便您可以偵錯，請遵循本主題中的所有步驟。

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>建立 ASP.NET 4.5.2 Visual Studio 電腦上的應用程式

1. 建立新的 MVC ASP.NET 應用程式。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019，輸入**Ctrl + Q**來開啟 搜尋 方塊中，輸入**asp.net**，選擇 **範本**，然後選擇 **建立新 ASP.NET Web 應用程式 (.NETFramework)**。 在出現的對話方塊中，為專案名稱**MyASPApp**，然後選擇**建立**。 選取  **MVC** ，然後選擇**建立**。
    ::: moniker-end
    ::: moniker range="vs-2017"
    若要在 Visual Studio 2017 中這樣做，請選擇**檔案 > 新增 > 專案**，然後選取**視覺化C#> Web > ASP.NET Web 應用程式**。 在 [ASP.NET 4.5.2]  範本區段中選取 [MVC] 。 請確定**啟用 Docker 支援**未選取且**驗證**設定為**不需要驗證**。 將專案命名為**MyASPApp**。)
    ::: moniker-end

2. 開啟 HomeController.cs 檔案，並在 `About()` 方法中設定中斷點。

## <a name="bkmk_configureIIS"></a> 安裝及設定 Windows Server 上的 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中 （它預設啟用），已啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，可讓您下載某些網頁伺服器元件。 新增信任的網站，方法是前往**網際網路選項 > 安全性 > 受信任的站台 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，您可能會收到負載各種 web 站台指令碼和資源的權限授與的要求。 其中一些資源並不需要，但若要簡化程序中，按一下**新增**出現提示時。

## <a name="BKMK_deploy_asp_net"></a> Windows Server 上安裝 ASP.NET 4.5

如果您想要在 IIS 上安裝 ASP.NET 的詳細的資訊，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

1. 在左窗格的 伺服器管理員中，選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取 [Internet Information Services (IIS) 管理員]。

1. 使用 Web Platform Installer (WebPI) 安裝 ASP.NET 4.5 (從 [Windows Server 2012 R2 中的 [伺服器] 節點中，選擇**取得新的 Web 平台元件**]，然後搜尋適用於 ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > 如果您使用的 Windows Server 2008 R2，請安裝 ASP.NET 4，改為使用下列命令：

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 重新啟動系統 (或從命令提示字元依序執行 **net stop was /y** 和 **net start w3svc**，讓系統 PATH 的變更生效)。

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

應用程式部署成功之後，它應該會自動啟動。 如果應用程式從 Visual Studio 不會啟動，請在 IIS 中啟動應用程式。

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

5. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

6. 設定**別名**欄位設為**MyASPApp**，接受預設的應用程式集區 (**DefaultAppPool**)，並將**實體路徑**至**C:\Publish**。

7. 底下**連線**，選取**應用程式集區**。 開啟**DefaultAppPool**和應用程式集區欄位設為**ASP.NET v4.0** （ASP.NET 4.5 不是應用程式集區的選項）。

8. 在 IIS 管理員中選取站台後，選擇**編輯權限**，並確定該 IUSR、 IIS_IUSRS 或 設定應用程式集區是授權的使用者具有讀取與執行權限的使用者。 如果沒有這些使用者不存在，將 IUSR 新增為具有讀取與執行權限的使用者。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>發佈和部署應用程式發行至本機資料夾從 Visual Studio

您可以發佈和部署應用程式使用檔案系統或其他工具。

1. (ASP.NET 4.5.2)請確定 web.config 檔案會列出.NET Framework 的正確版本。  比方說，如果您的目標 ASP.NET 4.5.2，請確定在 web.config 中列出此版本。

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    例如，版本應該為 4.0，如果您安裝 ASP.NET 4，而不是 4.5.2。

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

5. 核取 [顯示所有使用者的處理序]  。

6. 輸入以快速找出處理序名稱的第一個字母**w3wp.exe**針對 ASP.NET 4.5。

    如果您有多個處理序顯示**w3wp.exe**，檢查**使用者名**資料行。 在某些情況下，**使用者名**資料行中顯示您應用程式集區的名稱，例如**IIS APPPOOL\DefaultAppPool**。 如果您會看到應用程式集區，輕鬆地找出正確的處理序是建立新應用程式集區命名為應用程式執行個體，您要偵錯，然後您可以找到它輕鬆地在**使用者名**資料行。

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. 按一下 [附加]

8. 開啟遠端電腦的網站。 在瀏覽器中，移至 **http://\<遠端電腦名稱>**。

    您應該會看到 ASP.NET 網頁。
9. 執行的 ASP.NET 應用程式中，按一下 連結**關於**頁面。

    應該在 Visual Studio 中叫用中斷點。

## <a name="bkmk_openports"></a> 疑難排解：在 Windows Server 上開啟必要的連接埠

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

2. 然後選擇**輸入規則 > 新的規則 > 通訊埠**。 選擇**下一步**下方，並在**特定本機連接埠**，輸入連接埠號碼，按一下**下一步**，然後**允許連線**，按一下 下一步，並新增名稱 (**IIS**， **Web Deploy**，或**msvsmon**) 的輸入規則。

    如果您想在 Windows 防火牆設定的更多詳細資料，請參閱[設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 建立其他必要的連接埠的其他規則。