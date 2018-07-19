---
title: 將發佈至 Azure 匯入發行設定
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808317"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>發行至 Azure App Service 應用程式匯入 Visual Studio 中發行設定

您可以使用**發佈**工具匯入發佈設定，然後再部署您的應用程式。 在本文中，我們會使用發佈設定，針對 Azure App Service，但您可以使用類似的步驟，匯入發行設定[IIS](../deployment/tutorial-import-publish-settings-iis.md)。 在某些情況下，使用的發行設定設定檔會加快速度比手動設定部署至 Visual Studio 的每個安裝的服務。

這些步驟適用於 Visual Studio 中的 ASP.NET、 ASP.NET Core 和.NET Core 應用程式。 您也可以匯入發行設定[Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)應用程式。 步驟對應至 Visual Studio 2017 15.6 版中。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 從 Azure App Service 中產生的發行設定檔
> * 發佈設定檔匯入 Visual Studio
> * 將應用程式部署至 Azure App Service

發行設定檔 (*\*.publishsettings*) 不同的發行設定檔 (*\*.pubxml*) 在 Visual Studio 中建立。 發行設定檔由 Azure App Service，然後它可以匯入 Visual Studio。

> [!NOTE]
> 如果您只需要複製 Visual Studio 發行設定檔 (*\*.pubxml*檔案)，您可以從一個到另一個 Visual Studio 的安裝，找到的發行設定檔 *\<profilename\>.pubxml*，請在 *\\< 專案名稱\>\Properties\PublishProfiles*適用於受管理的專案類型的資料夾。 若是網站，查看底下*\App_Data*資料夾。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 並**ASP.NET**並。**NET Framework**開發工作負載。 .NET Core 應用程式中，您也需要。**NET 核心**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

* 建立 Azure App Service。 如需詳細指示，請參閱[ASP.NET Core web 應用程式部署到 Azure 中使用 Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在電腦上執行 Visual Studio，請選擇**檔案** > **新專案**。

1. 在下**Visual C#** 或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**（僅限 C#) 或**ASP.NET Core Web 應用程式**，然後按一下 **確定**。

    如果看不到指定的專案範本，請按一下**開啟的 Visual Studio 安裝程式**的左窗格中的連結**新的專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 請參閱這篇文章，以識別所需的 Visual Studio 工作負載，您必須安裝的先決條件。

1. 選擇  **MVC** (.NET Framework) 或**Web 應用程式 （模型-檢視-控制器）** （適用於.NET Core)，並確定**非驗證**已選取，然後按一下**確定**。

1. 輸入名稱，例如**MyWebApp**然後按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置** > **建置方案**來建置專案。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>在 Azure App Service 中建立發行設定檔

1. 在 Azure 入口網站中，開啟 Azure App Service。

1. 按一下 **取得發行設定檔**並儲存在本機的設定檔。

    ![取得發行設定檔](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    副檔名 *.publishsettings*副檔名已產生在您儲存它的位置。 下列程式碼顯示檔案 （位於更容易閱讀的格式） 的部分的範例。

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
    一般而言，上述的 *.publishsettings 檔案包含您可以使用 Visual Studio 中，一個用來使用 Web Deploy，另一個来使用 FTP 部署部署中的兩個發行設定檔。 上述程式碼顯示的 Web Deploy 的設定檔。 稍後將匯入這兩個設定檔，當您匯入設定檔。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>匯入 Visual Studio 中的發佈設定和部署

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>後續步驟

在本教學課程中，您可以建立發行設定檔，它匯入到 Visual Studio 中，並部署至 Azure App Service 的 ASP.NET 應用程式。 您可以在 Visual Studio 中的發行選項的概觀。

> [!div class="nextstepaction"]
> [第一眼部署](../deployment/deploying-applications-services-and-components.md)
