---
title: 匯入發行設定以發行至 IIS
description: 建立和匯入發佈設定檔，以將應用程式從 Visual Studio 部署到 IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e0c7309f52fbc8056f09e5a59afcfdefaa8d0bf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "65680131"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>在 Visual Studio 中匯入發行設定，即可將應用程式發行至 IIS

您可以使用 [發行]**** 工具匯入發行設定，然後部署您的應用程式。 在本文中，我們會使用 IIS 的發行設定，但您可以使用類似步驟匯入 [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md) 的發行設定。 在某些情況下，使用發行設定的設定檔速度，比起針對每個 Visual Studio 安裝手動設定 IIS 部署還要快。

這些步驟適用於 Visual Studio 中的 ASP.NET、ASP.NET Core 和 .NET Core 應用程式。

在本教學課程中，您將：

> [!div class="checklist"]
> * 設定 IIS，讓您能夠產生發行設定檔案
> * 建立發行設定檔案
> * 將發行設定檔案匯入 Visual Studio
> * 將應用程式部署至 IIS

發佈設置檔 （*\*.publish 設置*） 與在 Visual Studio 中創建的發佈設定檔 （*\*.pubxml*） 不同。 發行設定檔案是由 IIS 或 Azure App Service 所建立，或者可以手動方式建立，並可匯入至 Visual Studio 中。

> [!NOTE]
> 如果您只需要將 Visual Studio 發佈設定檔 （.pubxml\*檔） 從 Visual Studio 的一個安裝複製到另一個安裝，則可以在*\\<專案名\>_屬性_發佈設定檔*資料夾中找到用於託管專案類型的發佈設定檔。 * \< \> * 針對網站，請查看 *\App_Data* 資料夾底下的內容。 發行設定檔是 MSBuild XML 檔案。

## <a name="prerequisites"></a>必要條件

::: moniker range=">=vs-2019"

* 您必須安裝 Visual Studio 2019 及 **ASP.NET 與網頁程式開發**工作負載。

    如果您尚未安裝 Visual Studio，請轉到 Visual [Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面以免費安裝它。
::: moniker-end

::: moniker range="vs-2017"

* 您必須安裝 Visual Studio 2017 以及 **ASP.NET 和 Web 開發**工作負載。

    如果您尚未安裝 Visual Studio，請轉到 Visual [Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面以免費安裝它。
::: moniker-end

* 在您的伺服器上，您必須執行 Windows Server 2012 或 Windows Server 2016，且必須正確安裝 [IIS 網頁伺服器角色](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (產生發行設定檔案 (*\*.publishsettings*) 時需要此角色)。 另外還必須在伺服器上安裝 ASP.NET 4.5 或 ASP.NET Core。 若要設定 ASP.NET 4.5，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。 若要設定 ASP.NET Core，請參閱[在使用 IIS 的 Windows 上裝載 ASP.NET Core](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>在 Visual Studio 中建立新的 ASP.NET 專案

1. 在執行 Visual Studio 的電腦上，建立新的專案。

    選擇正確的範本。 在本範例中，選擇 [ASP.NET Web 應用程式 (.NET Framework)]**** 或 (僅限 C#) [ASP.NET Core Web 應用程式]****，然後按一下 [確定]****。

    如果您沒有看到特定的專案範本，請在 [新增專案]**** 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式]**** 連結。 Visual Studio 安裝程式即會啟動。 安裝**ASP.NET和 Web 開發**工作負載。

    您選擇的專案範本 (ASP.NET 或 ASP.NET Core) 必須與 Web 伺服器上所安裝的 ASP.NET 版本相對應。

1. 選擇 [MVC]**** (.NET Framework) 或 [Web 應用程式 (Model-View-Controller)]**** (適用於 .NET Core)，並確定已選取 [不需要驗證]****，然後按一下 [確定]****。

1. 鍵入 **MyWebApp** 這類名稱，然後按一下 [確定]****。

    Visual Studio 會建立專案。

1. 選擇**生成** > **生成解決方案**來生成專案。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>在 Windows Server 上安裝並設定 Web Deploy

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>在 Windows Server 上的 IIS 中建立發行設定檔案

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>在 Visual Studio 中匯入發行設定並進行部署

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

應用程式部署成功之後，它應該會自動啟動。 如果沒有從 Visual Studio 啟動，請在 IIS 中啟動該應用程式。 針對 ASP.NET Core，您必須先確定**DefaultAppPool** 的 [應用程式集區] 欄位設定為 [沒有受控程式碼]****。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已建立發行設定檔案、將其匯入至 Visual Studio 中，並已將 ASP.NET 應用程式部署至 IIS。 您可能需要 Visual Studio 中的其他發行選項概觀。

> [!div class="nextstepaction"]
> [部署簡介](../deployment/deploying-applications-services-and-components.md)
