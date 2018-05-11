---
title: 發行至 IIS 藉由匯入發行設定
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1db8ca68453cff105f2bbefcd384b8afa9efea9d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>發行至 IIS 應用程式匯入 Visual Studio 中發行設定

您可以使用**發行**工具匯入發行設定，然後再部署您的應用程式。 在本文中，我們會使用發行設定 IIS，但您可以使用類似的步驟，匯入發行設定[Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)。 在某些情況下，使用的發行設定設定檔會加快速度比手動設定部署至 IIS 的每個 Visual Studio 的安裝。

這些步驟適用於 Visual Studio 中的 ASP.NET、 ASP.NET Core 和.NET Core 應用程式。 步驟對應至 Visual Studio 2017 15.6 版本。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 設定 IIS，讓您可以產生的發行設定檔
> * 建立的發行設定檔
> * 發行設定檔匯入 Visual Studio
> * 將應用程式部署至 IIS

發行設定檔 (\*.publishsettings) 不同於發行設定檔 (\*.pubxml) 在 Visual Studio 中建立。 發行設定檔由 IIS 或 Azure 應用程式服務，或它可以手動建立，並接著可以將它匯入到 Visual Studio。

> [!NOTE]
> 如果您只需要複製 Visual Studio 發行設定檔 (\*.pubxml 檔案) 從一個到另一個 Visual Studio 的安裝，您可以找到發行設定檔，  *\<profilename\>.pubxml*，在 *\\< 專案名稱\>\Properties\PublishProfiles* managed 的專案類型的資料夾。 對於網站，查看  *\App_Data*資料夾。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

* 您必須已安裝的 Visual Studio 和**ASP.NET**和 **.NET Framework**開發工作負載。 .NET Core 應用程式中，您也需要 **.NET Core**工作負載。

    如果您尚未安裝 Visual Studio，請在[這裡](http://www.visualstudio.com)免費安裝它。

    這篇文章中的步驟會根據 Visual Studio 2017

* 若要從 IIS 中產生的發行設定檔案，您必須正確設定 IIS 8.0 網頁伺服器角色與其中一個 ASP.NET 4.5 執行 Windows Server 2012 的另一部電腦或 ASP.NET Core 安裝。 適用於 ASP.NET Core，請參閱[發行至 IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。 針對 ASP.NET 4.5，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在電腦上執行 Visual Studio，選擇 **檔案 > 新的專案**。

1. 在下**Visual C#** 或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**（僅限 C#) 或**ASP.NET Core Web 應用程式**，然後按一下 **確定**。

    如果看不到指定的專案範本，按一下**開啟 Visual Studio 安裝程式**的左窗格中的連結**新專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 請參閱這篇文章，以識別所需的 Visual Studio 工作負載，您必須安裝的必要條件。

1. 選擇  **MVC** (.NET Framework) 或**Web 應用程式 （模型-檢視-控制器）** （適用於.NET Core)，並確定**非驗證**已選取，然後按一下**確定**。

1. 輸入的名稱，例如**MyWebApp**按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置 > 建置方案**建置專案。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>安裝和設定 Windows Server 上的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立的發行設定檔案

1. 在 IIS 中，以滑鼠右鍵按一下**Default Web Site**，選擇**部署** > **設定 Web 部署發行**。

    ![設定 Web Deploy 設定](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. 在**設定 Web 部署發行**對話方塊方塊中，檢查設定。

1. 按一下**安裝**。

    在**結果**面板中，輸出中顯示的存取權限已授與指定的使用者，而且副檔名 *.publishsettings*中顯示的位置中產生檔案的副檔名對話方塊。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    根據您的 Windows Server 和 IIS 設定，您會看到不同的值。 以下是一些詳細資料，您所看到的值：

    * *Msdeploy.axd*檔案中參考`publishUrl`屬性為 Web deploy 以動態方式產生 HTTP 處理常式檔案。 (基於測試目的，`http://myhostname:8172`通常也可以使用。)
    * `publishUrl`連接埠通常設定為連接埠 8172，Web deploy 預設值。
    * `destinationAppUrl`連接埠通常設定為連接埠 80，此為 IIS 的預設值。
    * 如果無法連線至遠端主機使用的主機名稱 （在稍後步驟中） 的 Visual Studio 中，測試來取代主機名稱的 IP 位址。

    > [!NOTE]
    > 如果您要發行至 Azure VM 上執行之 IIS，Web Deploy 與 IIS 通訊埠必須開啟網路安全性群組中。 如需詳細資訊，請參閱[安裝和執行的 IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic)。

1. 將這個檔案複製到執行 Visual Studio 的電腦。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>匯入 Visual Studio 中的發行設定和部署

1. 在電腦上有 Visual Studio 中開啟 ASP.NET 專案的位置，以滑鼠右鍵按一下方案總管] 中的專案，然後選擇 [**發行**。

1. 如果您先前設定的任何發行設定檔，**發行** 窗格隨即出現。 按一下**建立新的設定檔**。

1. 在**挑選發行目標**對話方塊中，按一下 **匯入設定檔**。

    ![選擇發行](../deployment/media/tutorial-publish-tool-import-profile.png)

1. 瀏覽至您在上一節中建立的發行設定檔案的位置。

1. 在**匯入發行設定檔**對話方塊中，瀏覽至並選取您在上一節中建立的設定檔，然後按一下**開啟**。

    Visual Studio 開始部署程序，和 [輸出] 視窗會顯示進度和結果。

    如果您取得的任何部署錯誤，請按一下**設定**編輯設定。 修改設定，然後按一下**驗證**來測試新的設定。

    ![在發行工具中編輯設定](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您可以建立的發行設定檔，它匯入到 Visual Studio 中，並部署至 IIS 的 ASP.NET 應用程式。

> [!div class="nextstepaction"]
> [第一眼部署](../deployment/deploying-applications-services-and-components.md)
