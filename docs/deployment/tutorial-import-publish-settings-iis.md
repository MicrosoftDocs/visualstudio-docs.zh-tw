---
title: 發行至 IIS，藉由匯入發行設定
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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808461"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>發行至 IIS 應用程式匯入 Visual Studio 中發行設定

您可以使用**發佈**工具匯入發佈設定，然後再部署您的應用程式。 在本文中，我們會使用發佈設定 iis，但您可以使用類似的步驟，匯入發行設定[Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)。 在某些情況下，使用的發行設定設定檔會加快速度比手動設定部署至 IIS 的每個 Visual Studio 的安裝。

這些步驟適用於 Visual Studio 中的 ASP.NET、 ASP.NET Core 和.NET Core 應用程式。 步驟對應至 Visual Studio 2017 15.6 版中。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 設定 IIS，讓您可以產生發佈設定檔
> * 建立發行設定檔
> * 發佈設定檔匯入 Visual Studio
> * 將應用程式部署至 IIS

發行設定檔 (*\*.publishsettings*) 不同的發行設定檔 (*\*.pubxml*) 在 Visual Studio 中建立。 發行設定檔由 IIS 或 Azure App Service，或可以手動建立，然後到 Visual Studio 再可以匯入。

> [!NOTE]
> 如果您只需要複製 Visual Studio 發行設定檔 (\*.pubxml 檔案) 從一個到另一個 Visual Studio 的安裝，您可以找到發行設定檔中，  *\<profilename\>.pubxml*，在   *\\< 專案名稱\>\Properties\PublishProfiles*適用於受管理的專案類型的資料夾。 若是網站，查看底下*\App_Data*資料夾。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 並**ASP.NET**並 **.NET Framework**開發工作負載。 .NET Core 應用程式中，您也需要 **.NET Core**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

* 若要從 IIS 產生發佈設定檔，您必須執行 Windows Server 2012 或 Windows Server 2016 的電腦，您必須正確設定的 IIS 網頁伺服器角色。 也必須安裝 ASP.NET 4.5 或 ASP.NET Core。 針對 ASP.NET Core，請參閱[Publishing to IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。 針對 ASP.NET 4.5，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在電腦上執行 Visual Studio，請選擇**檔案** > **新專案**。

1. 在下**Visual C#** 或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**（僅限 C#) 或**ASP.NET Core Web 應用程式**，然後按一下 **確定**。

    如果看不到指定的專案範本，請按一下**開啟的 Visual Studio 安裝程式**的左窗格中的連結**新的專案** 對話方塊。 Visual Studio 安裝程式即會啟動。 請參閱這篇文章，以識別所需的 Visual Studio 工作負載，您必須安裝的先決條件。

1. 選擇  **MVC** (.NET Framework) 或**Web 應用程式 （模型-檢視-控制器）** （適用於.NET Core)，並確定**非驗證**已選取，然後按一下**確定**。

1. 輸入名稱，例如**MyWebApp**然後按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置** > **建置方案**來建置專案。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>安裝和設定 Windows Server 上的 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>匯入 Visual Studio 中的發佈設定和部署

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果沒有啟動從 Visual Studio，請在 IIS 中啟動應用程式。 您需要確定應用程式集區欄位的 ASP.NET Core **DefaultAppPool**設**沒有 Managed 程式碼**。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您可以建立發行設定檔，它匯入到 Visual Studio 中，並部署至 IIS 的 ASP.NET 應用程式。 您可以在 Visual Studio 中的其他發行選項的概觀。

> [!div class="nextstepaction"]
> [第一眼部署](../deployment/deploying-applications-services-and-components.md)
