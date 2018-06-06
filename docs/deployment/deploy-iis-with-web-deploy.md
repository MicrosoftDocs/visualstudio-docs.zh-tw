---
title: 將 ASP.NET 部署到 IIS 使用 Web Deploy
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794192"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>將 ASP.NET 部署至遠端 IIS 的電腦使用 Visual Studio 中的 Web Deploy

本文說明如何安裝和設定 Visual Studio 2017 ASP.NET MVC 4.5.2 應用程式，並將它部署到 IIS。 這篇文章包含基本的 Windows server 上的 IIS 組態設定及部署 Visual Studio 應用程式的步驟。 這些步驟是以確定伺服器具有必要安裝元件，而且您準備好要部署。 如果您要部署 ASP.NET Core 應用程式，某些步驟將會不同。 若要部署 ASP.NET Core 應用程式，請參閱[發行至 IIS 的應用程式，藉由匯入發行設定](../deployment/tutorial-import-publish-settings-iis.md)如需相關指示。 在某些 ASP.NET 和 ASP.NET Core 的情況下，它會比部署到 IIS 藉由匯入發行設定。

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 8 （Windows Server 2008 R2，則伺服器步驟會不同）

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>建立 ASP.NET 4.5.2 Visual Studio 電腦上的應用程式
  
1. 在電腦上執行 Visual Studio，選擇 **檔案 > 新的專案**。

1. 在下**Visual C#** 或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**，然後按一下 **確定**。

    如果看不到指定的專案範本，按一下**開啟 Visual Studio 安裝程式**的左窗格中的連結**新專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 請參閱這篇文章，以識別所需的 Visual Studio 工作負載，您必須安裝的必要條件。

1. 選擇**MVC** (.NET Framework)，請確定**非驗證**已選取，然後按一下**確定**。

1. 輸入的名稱，例如**MyWebApp**按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置 > 建置方案**建置專案。

## <a name="bkmk_configureIIS"></a> 安裝及設定 Windows Server 上的 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer （它預設會啟用） 啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，您可以下載某些網頁伺服器元件。 新增信任的網站，請前往**網際網路選項 > 安全性 > 受信任的網站 > 網站**。 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，可能會收到要求授與權限來載入各種網站指令碼和資源。 其中一些資源並非必要，但若要簡化程序中，按一下**新增**出現提示時。

## <a name="BKMK_deploy_asp_net"></a> Windows 伺服器上安裝 ASP.NET 4.5

如果您想要在 IIS 上安裝 ASP.NET 的詳細的資訊，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

1. 在左窗格的 伺服器管理員中，選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取**網際網路資訊服務 (IIS) 管理員**。

1. 使用 Web Platform Installer (WebPI) 安裝 ASP.NET 4.5 (從 Windows Server 2012 R2 中的 伺服器 節點，選擇 **取得新的 Web 平台元件**ASP.NET 然後搜尋)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > 如果您使用 Windows Server 2008 R2，請安裝 ASP.NET 4，改為使用這個命令：

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 重新啟動系統 (或執行**net stop was /y**後面**net 啟動 w3svc**挑選變更到系統路徑的命令提示字元)。

## <a name="BKMK_install_webdeploy"></a> 安裝 Web Deploy 3.6 Windows 伺服器上

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> 設定 Windows Server 電腦上的 ASP.NET 網站

1. 開啟 Windows 檔案總管，並建立新的資料夾， **C:\Publish**將稍後部署 ASP.NET 專案。

2. 如果它尚未開啟，開啟**網際網路資訊服務 (IIS) 管理員**。 (在伺服器管理員 的左窗格中選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取**網際網路資訊服務 (IIS) 管理員**。)

3. 在下**連線**在左窗格中，移至**網站**。

4. 選取**Default Web Site**，選擇**基本設定**，並設定**實體路徑**至**C:\Publish**。

5. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

6. 設定**別名**欄位設為**MyASPApp**，接受預設的應用程式集區 (**DefaultAppPool**)，並設定**實體路徑**至**C:\Publish**。

7. 在下**連線**，選取**應用程式集區**。 開啟**DefaultAppPool**並將應用程式集區欄位設定為**ASP.NET v4.0** （ASP.NET 4.5 不是應用程式集區的選項）。

8. 在 IIS 管理員中選取站台之後，選擇 **編輯權限**，並確定該 IUSR、 IIS_IUSRS 或設定為應用程式集區授權的使用者具有讀取和執行權限的使用者。 如果沒有存在這些使用者，新增 IUSR 具有讀取和執行權限的使用者身分。

## <a name="bkmk_webdeploy"></a> 發行和部署使用 Web Deploy 從 Visual Studio 的應用程式

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

此外，您可能需要閱讀上一節[疑難排解連接埠](#bkmk_openports)。

## <a name="bkmk_openports"></a> 疑難排解： 開啟 Windows Server 上的必要連接埠

大部分的安裝中安裝 ASP.NET 和 Web Deploy 所開啟必要的連接埠。 不過，您可能需要確認連接埠已開啟。

> [!NOTE]
> 在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)。 

必要的連接埠：

* 80-所需的 IIS
* 8172-所需的 Web Deploy 來部署應用程式，從 Visual Studio

1. 若要開啟 Windows Server 上的連接埠，請開啟**啟動**功能表中，搜尋**具有進階安全性的 Windows 防火牆**。

2. 然後選擇 **輸入規則 > 新的規則 > 通訊埠**。 選擇**下一步**下方和 **特定本機連接埠**，輸入連接埠號碼，按一下**下一步**，然後**允許連線**，按一下 下一步，和新增名稱 (**IIS**， **Web Deploy**，或**msvsmon**) 的輸入規則。

    如果您想需設定 Windows 防火牆的詳細資訊，請參閱[設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 建立其他必要的連接埠的其他規則。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您可以建立的發行設定檔，它匯入到 Visual Studio 中，並部署至 IIS 的 ASP.NET 應用程式。 您也可以部署藉由匯入發行設定。

> [!div class="nextstepaction"]
> [將部署到 IIS 藉由匯入發行設定](../deployment/tutorial-import-publish-settings-iis.md)