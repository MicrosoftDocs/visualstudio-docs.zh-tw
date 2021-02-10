---
title: 匯入發行設定以發行至 Azure
description: 建立和匯入發佈設定檔，以將應用程式從 Visual Studio 部署到 Azure App Service
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50a65d681693bd9c1421767d2cac47f65b685e6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945041"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>在 Visual Studio 中匯入發行設定，即可將應用程式發行至 Azure App Service

您可以使用 [發行] 工具匯入發行設定，然後部署您的應用程式。 在本文中，我們會使用 Azure App Service 的發行設定，但您可以使用類似步驟從 [IIS](../deployment/tutorial-import-publish-settings-iis.md) 匯入發行設定。 在某些情況下，使用發行設定的設定檔速度，比起針對每個 Visual Studio 安裝手動設定服務部署還要快。

這些步驟適用於 Visual Studio 中的 ASP.NET、ASP.NET Core 和 .NET Core 應用程式。 您也可以匯入 [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) 應用程式的發行設定。

在本教學課程中，您將：

> [!div class="checklist"]
> * 從 Azure App Service 中產生發行設定檔案
> * 將發行設定檔案匯入 Visual Studio
> * 將應用程式部署至 Azure App Service

發行設定檔案 (*\* .Publishsettings*) 與 (的發行設定檔不同 *\* 。 .Pubxml*) 在 Visual Studio 中建立。 發行設定檔案是由 Azure App Service 所建立，並可匯入至 Visual Studio。

> [!NOTE]
> 如果您只需要將 Visual Studio 發行配置)  (檔從一個 Visual Studio 安裝複製到另一個，您可以在 [managed 專案類型] 的 [ *\\<專案名稱 \> \Properties\PublishProfiles* ] 資料夾中找到發行 *\* 設定檔* *\<profilename\> .pubxml*。 針對網站，請查看 *\App_Data* 資料夾底下的內容。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"

* 您必須安裝 Visual Studio 2019 及 **ASP.NET 與網頁程式開發** 工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
::: moniker-end

::: moniker range="vs-2017"

* 您必須安裝 Visual Studio 2017 以及 **ASP.NET 和 Web 開發** 工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
::: moniker-end

* 建立 Azure App Service。 如需詳細指示，請參閱[使用 Visual Studio 將 ASP.NET Core Web 應用程式部署至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在執行 Visual Studio 的電腦上，建立新的專案。

    選擇正確的範本。 在此範例中，請選擇 [ **ASP.NET Web 應用程式 (] .NET Framework)** 或 ([僅限 c #) **Web 應用程式**]，然後選取 **[確定]**。

    如果您沒有看到指定的專案範本，請移至 [**新增專案**] 對話方塊左窗格中的 [**開啟 Visual Studio 安裝程式**] 連結。 Visual Studio 安裝程式即會啟動。 安裝 **ASP.NET 和 網頁程式開發** 工作負載。

    您選擇的專案範本 (ASP.NET 或 ASP.NET Core) 必須與 Web 伺服器上所安裝的 ASP.NET 版本相對應。

1. 選擇 [ **MVC** ( .NET Framework) ] 或 [ **Web 應用程式] (模型-視圖-控制器)** (適用于 .net Core) ，並確定 **未** 選取 [驗證]，然後選取 **[確定]**。

1. 輸入名稱，例如 **MyWebApp** ，然後選取 **[確定]**。

    Visual Studio 會建立專案。

1. 選擇 [**組建**  >  **組建方案**] 以建立專案。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>在 Azure App Service 中建立發行設定檔案

1. 在 Azure 入口網站中開啟 Azure App Service。

1. 移至 [ **取得發行設定檔** ]，並將設定檔儲存在本機。

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

## <a name="next-steps"></a>下一步

在本教學課程中，您已建立發行設定檔案、將其匯入至 Visual Studio，並已將 ASP.NET 應用程式部署至 Azure App Service。 您可能需要 Visual Studio 中發行選項的概觀。

> [!div class="nextstepaction"]
> [部署簡介](../deployment/deploying-applications-services-and-components.md)
