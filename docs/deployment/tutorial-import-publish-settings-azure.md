---
title: 發行至 Azure 匯入發行設定
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 88dc37e555f6ceb30584d4a1c17b96506219631a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766736"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>發行至 Azure App Service 應用程式匯入 Visual Studio 中發行設定

您可以使用**發行**工具匯入發行設定，然後再部署您的應用程式。 在本文中，我們會使用發行 Azure 應用程式服務設定，但是您可以使用類似的步驟，匯入發行設定[IIS](../deployment/tutorial-import-publish-settings-iis.md)。 在某些情況下，使用的發行設定設定檔會加快速度比手動設定部署至 Visual Studio 的每個安裝的服務。

這些步驟適用於 Visual Studio 中的 ASP.NET、 ASP.NET Core 和.NET Core 應用程式。 您也可以匯入發行設定[Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio)應用程式。 步驟對應至 Visual Studio 2017 15.6 版本。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 從 Azure 應用程式服務產生的發行設定檔
> * 發行設定檔匯入 Visual Studio
> * 將應用程式部署至 Azure App Service

發行設定檔 (*\*.publishsettings*) 不同於發行設定檔 (*\*.pubxml*) 在 Visual Studio 中建立。 Azure 應用程式服務，會建立發行設定檔，然後可以將它匯入到 Visual Studio。

> [!NOTE]
> 如果您只需要複製 Visual Studio 發行設定檔 (*\*.pubxml*檔案) 從一個到另一個 Visual Studio 的安裝，您可以找到發行設定檔，  *\<profilename\>.pubxml*，請在 *\\< 專案名稱\>\Properties\PublishProfiles* managed 的專案類型的資料夾。 對於網站，查看  *\App_Data*資料夾。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 和**ASP.NET**和。**NET Framework**開發工作負載。 .NET Core 應用程式中，您也需要。**NET 核心**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

* 建立 Azure 的應用程式服務。 如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在電腦上執行 Visual Studio，選擇 **檔案 > 新的專案**。

1. 在下**Visual C#** 或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**（僅限 C#) 或**ASP.NET Core Web 應用程式**，然後按一下 **確定**。

    如果看不到指定的專案範本，按一下**開啟 Visual Studio 安裝程式**的左窗格中的連結**新專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 請參閱這篇文章，以識別所需的 Visual Studio 工作負載，您必須安裝的必要條件。

1. 選擇  **MVC** (.NET Framework) 或**Web 應用程式 （模型-檢視-控制器）** （適用於.NET Core)，並確定**非驗證**已選取，然後按一下**確定**。

1. 輸入的名稱，例如**MyWebApp**按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置 > 建置方案**建置專案。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>在 Azure App Service 中建立的發行設定檔案

1. 在 Azure 入口網站中，開啟 Azure 應用程式服務。

1. 按一下**取得發行設定檔**並儲存在本機上的設定檔。

    ![取得發行設定檔](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    具有檔案 *.publishsettings*已儲存位置的位置中產生檔案的副檔名。 下列程式碼顯示的檔案 （如果您以更容易閱讀的格式） 的部分範例。

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    一般而言，上述 *.publishsettings 檔案包含兩個您可以使用 Visual Studio 中，一個使用 Web Deploy，和一個来使用 FTP 部署部署中的發行設定檔。 上述程式碼中顯示的 Web Deploy 設定檔。 稍後將會匯入這兩個設定檔，當您匯入設定檔。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>匯入 Visual Studio 中的發行設定和部署

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>後續步驟

在本教學課程中，您建立的發行設定檔、 Visual studio，將它匯入和 ASP.NET 應用程式部署至 Azure App Service。 您可以在 Visual Studio 中的發佈選項的概觀。

> [!div class="nextstepaction"]
> [第一眼部署](../deployment/deploying-applications-services-and-components.md)
