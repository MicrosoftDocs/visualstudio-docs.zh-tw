---
title: 匯入發行設定以發行至 Azure
description: 建立和匯入發佈設定檔，以將應用程式從 Visual Studio 部署到 Azure App Service
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be70da79b1edc6142be1c45464097a027f859979
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413562"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>在 Visual Studio 中匯入發行設定，即可將應用程式發行至 Azure App Service

您可以使用 [發行] 工具匯入發行設定，然後部署您的應用程式。 在本文中，我們會使用 Azure App Service 的發行設定，但您可以使用類似步驟從 [IIS](../deployment/tutorial-import-publish-settings-iis.md) 匯入發行設定。 在某些情況下，使用發行設定的設定檔速度，比起針對每個 Visual Studio 安裝手動設定服務部署還要快。

這些步驟適用於 Visual Studio 中的 ASP.NET、ASP.NET Core 和 .NET Core 應用程式。 您也可以匯入 [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) 應用程式的發行設定。 這些步驟對應於 Visual Studio 2017 15.6 版。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 從 Azure App Service 中產生發行設定檔案
> * 將發行設定檔案匯入 Visual Studio
> * 將應用程式部署至 Azure App Service

發行設定檔案 (*\*.publishsettings*) 不同於 Visual Studio 中建立的發行設定檔 (*\*.pubxml*)。 發行設定檔案是由 Azure App Service 所建立，並可匯入至 Visual Studio。

> [!NOTE]
> 如果您只需要從某個 Visual Studio 安裝將 Visual Studio 發行設定檔 (*\*.pubxml* 檔案) 複製到另一個 Visual Studio 安裝，您可以在受控專案類型的 \\<專案名稱\>\Properties\PublishProfiles 資料夾中找到發行設定檔 \<設定檔名稱\>.pubxml。 針對網站，請查看 *\App_Data* 資料夾底下的內容。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 以及 **ASP.NET 和 Web 開發**工作負載。

    如果您尚未安裝 Visual Studio，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) 頁面免費進行安裝。

* 建立 Azure App Service。 如需詳細指示，請參閱[使用 Visual Studio 將 ASP.NET Core Web 應用程式部署至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在執行 Visual Studio 的電腦上，選擇 [檔案] > [新增專案]。

1. 在 [Visual C#] 或 [Visual Basic] 底下，選擇 [Web]，然後在中間窗格中選擇 [ASP.NET Web 應用程式 (.NET Framework)] 或 (僅限於 C#) [ASP.NET Core Web 應用程式]，然後按一下 [確定]。

    如果您沒有看到特定的專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 安裝 **ASP.NET 和 Web 開發**工作負載。

    您選擇的專案範本 (ASP.NET 或 ASP.NET Core) 必須與 Web 伺服器上所安裝的 ASP.NET 版本相對應。

1. 選擇 [MVC] (.NET Framework) 或 [Web 應用程式 (Model-View-Controller)] (適用於 .NET Core)，並確定已選取 [不需要驗證]，然後按一下 [確定]。

1. 鍵入 **MyWebApp** 這類名稱，然後按一下 [確定]。

    Visual Studio 會建立專案。

1. 選擇 [建置] > [建置方案] 來建置專案。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>在 Azure App Service 中建立發行設定檔案

1. 在 Azure 入口網站中開啟 Azure App Service。

1. 按一下 [取得發行設定檔]，並在本機儲存設定檔。

    ![取得發行設定檔](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    已在檔案儲存位置產生副檔名為 *.publishsettings* 的檔案。 下列程式碼顯示檔案的部分範例 (使用更容易閱讀的格式)。

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
    一般而言，上述的 *.publishsettings 檔案包含兩個您可以在 Visual Studio 中使用的發行設定檔，一個使用 Web Deploy 進行部署，另一個則使用 FTP 進行部署。 上述程式碼會顯示 Web Deploy 設定檔。 當您匯入設定檔時，稍後將匯入這兩個設定檔。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立發行設定檔案、將其匯入至 Visual Studio，並已將 ASP.NET 應用程式部署至 Azure App Service。 您可能需要 Visual Studio 中發行選項的概觀。

> [!div class="nextstepaction"]
> [第一眼部署](../deployment/deploying-applications-services-and-components.md)
