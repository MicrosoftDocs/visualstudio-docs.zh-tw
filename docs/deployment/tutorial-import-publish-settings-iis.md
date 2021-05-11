---
title: 匯入發行設定以發行至 IIS
description: 建立和匯入發佈設定檔，以將應用程式從 Visual Studio 部署到 IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aeaaff68ab0abe85838456e8c8b69e2520295689
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729269"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>在 Visual Studio 中匯入發行設定，即可將應用程式發行至 IIS

您可以使用 [發行] 工具匯入發行設定，然後部署您的應用程式。 在本文中，我們會使用 IIS 的發行設定，但您可以使用類似步驟匯入 [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md) 的發行設定。 在某些情況下，使用發行設定的設定檔速度，比起針對每個 Visual Studio 安裝手動設定 IIS 部署還要快。

這些步驟適用於 Visual Studio 中的 ASP.NET、ASP.NET Core 和 .NET Core 應用程式。

在本教學課程中，您將：

> [!div class="checklist"]
> * 設定 IIS，讓您能夠產生發行設定檔案
> * 建立發行設定檔案
> * 將發行設定檔案匯入 Visual Studio
> * 將應用程式部署至 IIS

發行設定檔案 (*\* .Publishsettings*) 與 (的發行設定檔不同 *\* 。 .Pubxml*) 在 Visual Studio 中建立。 發行設定檔案是由 IIS 或 Azure App Service 所建立，或者可以手動方式建立，並可匯入至 Visual Studio 中。

> [!NOTE]
> 如果您只需要將 Visual Studio 發行配置)  (檔 \* 從一個 Visual Studio 安裝複製到另一個，您可以在 [managed 專案類型] 的 [ *\\<專案名稱 \> \Properties\PublishProfiles* ] 資料夾中找到發行設定檔 *\<profilename\> .pubxml*。 針對網站，請查看 *\App_Data* 資料夾底下的內容。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"

* 您必須安裝 Visual Studio 2019 及 **ASP.NET 與網頁程式開發** 工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
::: moniker-end

::: moniker range="vs-2017"

* 您必須安裝 Visual Studio 2017 以及 **ASP.NET 和 Web 開發** 工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
::: moniker-end

* 在您的伺服器上，您必須執行 Windows Server 2012、Windows Server 2016 或 Windows Server 2019，而且必須正確安裝 [IIS 網頁伺服器角色](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (才能產生發佈設定檔案 (*\* . .publishsettings*) ) 。 另外還必須在伺服器上安裝 ASP.NET 4.5 或 ASP.NET Core。 若要設定 ASP.NET 4.5，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。 若要設定 ASP.NET Core，請參閱[在使用 IIS 的 Windows 上裝載 ASP.NET Core](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。 針對 ASP.NET Core，請務必將應用程式集區設定為 **不使用 Managed 程式碼**，如本文中所述。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在執行 Visual Studio 的電腦上，建立新的專案。

    選擇正確的範本。 在此範例中，請選擇 [ **ASP.NET Web 應用程式 (] .NET Framework)** 或 ([僅限 c #) **Web 應用程式**]，然後選取 **[確定]**。

    如果您沒有看到指定的專案範本，請移至 [**新增專案**] 對話方塊左窗格中的 [**開啟 Visual Studio 安裝程式**] 連結。 Visual Studio 安裝程式即會啟動。 安裝 **ASP.NET 和 網頁程式開發** 工作負載。

    您選擇的專案範本 (ASP.NET 或 ASP.NET Core) 必須與 Web 伺服器上所安裝的 ASP.NET 版本相對應。

1. 選擇 [ **MVC** ( .NET Framework) ] 或 [ **Web 應用程式] (模型-視圖-控制器)** (適用于 .net Core) ，並確定 **未** 選取 [驗證]，然後選取 **[確定]**。

1. 輸入名稱，例如 **MyWebApp** ，然後選取 **[確定]**。

    Visual Studio 會建立專案。

1. 選擇 [**組建**  >  **組建方案** (]，或按 **Ctrl**  +  **Shift**  +  **B**) 以建立專案。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>在 Windows Server 上安裝並設定 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果沒有從 Visual Studio 啟動，請在 IIS 中啟動該應用程式。 針對 ASP.NET Core，您必須先確定 **DefaultAppPool** 的 [應用程式集區] 欄位設定為 [沒有受控程式碼]。

## <a name="next-steps"></a>下一步

在本教學課程中，您已建立發行設定檔案、將其匯入至 Visual Studio 中，並已將 ASP.NET 應用程式部署至 IIS。 您可能需要 Visual Studio 中的其他發行選項概觀。

> [!div class="nextstepaction"]
> [部署簡介](../deployment/deploying-applications-services-and-components.md)
