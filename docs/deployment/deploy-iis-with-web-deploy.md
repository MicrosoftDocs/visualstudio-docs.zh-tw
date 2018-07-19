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
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080846"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>將 ASP.NET 部署到遠端執行 IIS 的電腦使用 Visual Studio 中的 Web Deploy

這篇文章說明如何安裝和設定 Visual Studio 2017 ASP.NET MVC 4.5.2 應用程式並將它部署至 IIS。 這篇文章包含的基本組態中的 Windows server 上的 IIS 設定和部署應用程式從 Visual Studio 中的步驟。 這些步驟都包含在內，以確定伺服器具有必要安裝的元件，而且您準備好要部署。 如果您要部署的 ASP.NET Core 應用程式，則不同一些步驟。 若要部署 ASP.NET Core 應用程式，請參閱[發行至 IIS 的應用程式，藉由匯入發行設定](../deployment/tutorial-import-publish-settings-iis.md)如需相關指示。 在某些 ASP.NET 和 ASP.NET Core 的情況下，它會比部署至 IIS，藉由匯入發佈設定。

這些伺服器設定過這些程序：
* Windows Server 2012 R2 和 IIS 8 （Windows Server 2008 R2，伺服器的步驟並不等於）

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>建立 ASP.NET 4.5.2 Visual Studio 電腦上的應用程式
  
1. 在電腦上執行 Visual Studio，請選擇**檔案** > **新專案**。

1. 底下**Visual C#** 或是**Visual Basic**，選擇  **Web**，然後在中間窗格選擇  **ASP.NET Web 應用程式 (.NET Framework)**，然後按一下  **確定**。

    如果看不到指定的專案範本，請按一下**開啟的 Visual Studio 安裝程式**的左窗格中的連結**新的專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 請參閱這篇文章，以識別所需的 Visual Studio 工作負載，您必須安裝的先決條件。

1. 選擇**MVC** (.NET Framework) 並確認**不需要驗證**已選取，然後按一下**確定**。

1. 輸入名稱，例如**MyWebApp**然後按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置** > **建置方案**來建置專案。

## <a name="install-and-configure-iis-on-windows-server"></a>安裝及設定 Windows Server 上的 IIS

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>更新 Windows Server 上的瀏覽器安全性設定

如果在 Internet Explorer 中 （它預設啟用），已啟用增強式安全性設定，您可能需要將某些網域新增為信任的網站，可讓您下載某些網頁伺服器元件。 新增信任的網站，方法是前往**網際網路選項** > **安全性** > **受信任的站台** > **站台**. 新增下列網域。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

當您下載軟體時，您可能會收到負載各種 web 站台指令碼和資源的權限授與的要求。 其中一些資源並不需要，但若要簡化程序中，按一下**新增**出現提示時。

## <a name="install-aspnet-45-on-windows-server"></a>Windows Server 上安裝 ASP.NET 4.5

如果您想要在 IIS 上安裝 ASP.NET 的詳細的資訊，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

1. 在左窗格的 伺服器管理員中，選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取**Internet Information Services (IIS) 管理員**。

1. 使用 Web Platform Installer (WebPI) 安裝 ASP.NET 4.5 (從 [Windows Server 2012 R2 中的 [伺服器] 節點中，選擇**取得新的 Web 平台元件**]，然後搜尋適用於 ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > 如果您使用的 Windows Server 2008 R2，請安裝 ASP.NET 4，改為使用下列命令：

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. 重新啟動系統 (或執行**net stop was /y**後面**net start w3svc**挑選系統 PATH 的變更在命令提示字元)。

## <a name="install-web-deploy-36-on-windows-server"></a>安裝 Web Deploy Windows Server 上的 3.6

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>設定 Windows Server 電腦上的 ASP.NET 網站

1. 開啟 Windows 檔案總管，並建立新的資料夾中， **C:\Publish**將稍後部署 ASP.NET 專案。

2. 如果它尚未開啟，開啟**Internet Information Services (IIS) 管理員**。 (在左窗格的 伺服器管理員中，選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取**Internet Information Services (IIS) 管理員**。)

3. 底下**連線**在左窗格中，移至**站台**。

4. 選取  **Default Web Site**，選擇**基本設定**，並將**實體路徑**至**C:\Publish**。

5. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

6. 設定**別名**欄位設為**MyASPApp**，接受預設的應用程式集區 (**DefaultAppPool**)，並將**實體路徑**至**C:\Publish**。

7. 底下**連線**，選取**應用程式集區**。 開啟**DefaultAppPool**和應用程式集區欄位設為**ASP.NET v4.0** （ASP.NET 4.5 不是應用程式集區的選項）。

8. 在 IIS 管理員中選取站台後，選擇**編輯權限**，並確定該 IUSR、 IIS_IUSRS 或 設定應用程式集區是授權的使用者具有讀取與執行權限的使用者。 如果沒有這些使用者不存在，將 IUSR 新增為具有讀取與執行權限的使用者。

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>發佈和部署應用程式使用 Web Deploy 從 Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

此外，您可能需要閱讀下的一節有關如何疑難排解連接埠。

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>疑難排解： 開啟 Windows Server 上的必要連接埠

在大部分的配置，所需的連接埠已開啟 ASP.NET 和 Web Deploy 的安裝。 不過，您可能需要確認已開啟連接埠。

> [!NOTE]
> 在 Azure VM 中，您必須開啟連接埠通過[網路安全性群組](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)。 

必要的連接埠：

* 80-所需的 IIS
* 8172-所需的 Web Deploy 來部署應用程式從 Visual Studio

1. 若要開啟 Windows Server 上的連接埠，請開啟**開始**功能表中，搜尋**具有進階安全性的 Windows 防火牆**。

2. 然後選擇**輸入規則** > **新規則** > **連接埠**。 選擇**下一步**下方，並在**特定本機連接埠**，輸入連接埠號碼，按一下**下一步**，然後**允許連線**，按一下 下一步，並新增名稱 (**IIS**， **Web Deploy**，或**msvsmon**) 的輸入規則。

    如果您想在 Windows 防火牆設定的更多詳細資料，請參閱[設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

3. 建立其他必要的連接埠的其他規則。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您可以建立發行設定檔，它匯入到 Visual Studio 中，並部署至 IIS 的 ASP.NET 應用程式。 您也可以部署匯入發佈設定。

> [!div class="nextstepaction"]
> [部署至 IIS，藉由匯入發行設定](../deployment/tutorial-import-publish-settings-iis.md)
