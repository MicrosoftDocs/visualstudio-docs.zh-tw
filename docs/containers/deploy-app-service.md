---
title: 將ASP.NET核心 Docker 容器部署到 Azure 應用服務 |微軟文檔
description: 瞭解如何使用視覺化工作室容器工具將ASP.NET核心 Web 應用部署到 Azure 應用服務
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027295"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>使用視覺化工作室將ASP.NET核心容器部署到 Azure 應用服務

本教程將引導您完成使用 Visual Studio 將容器化ASP.NET核心 Web 應用程式發佈到[Azure 應用服務](/azure/app-service)。 Azure 應用服務是 Azure 中託管的單容器 Web 應用的適當服務。

如果您沒有 Azure 訂用帳戶，請在開始前建立[免費帳戶](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs)。

## <a name="prerequisites"></a>必要條件

若要完成本教學課程：

::: moniker range="vs-2017"
- 安裝包含 "ASP.NET 和 Web 開發" 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 最新版本
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，其中包含 *ASP.NET 和 Web 部署*工作負載。
::: moniker-end
- 安裝[Docker 桌面](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>建立 ASP.NET Core Web 應用程式

下列步驟會逐步引導您建立將在本教學課程中使用的基本 ASP.NET Core 應用程式。

::: moniker range="vs-2017"
1. 從 Visual Studio 功能表中，選取 [檔案] > [新增] > [專案]****。
2. 在 [新增專案]**** 對話方塊的 [範本]**** 區段下，選取 [Visual C#] > [Web]****。
3. 選取 **ASP.NET Core Web 應用程式**。
4. 指定新應用程式的名稱 (或使用預設值)，然後選取 [確定] ****。
5. 選擇**Web 應用程式**。
6. 請勾選 [啟用 Docker 支援]**** 核取方塊。
7. 選擇**Linux**容器類型，然後按一下 **"確定**"。 不支援將 Windows 容器作為容器部署到 Azure 應用服務。
::: moniker-end
::: moniker range=">= vs-2019"
1. 從 Visual Studio 的開始視窗中，選擇 [建立新專案]****。
1. 依序選擇 [ASP.NET Core Web 應用程式]**** 和 [下一步]****。
1. 指定新應用程式的名稱 (或使用預設)，然後選擇 [建立]****。
1. 選擇 [Web 應用程式]****。
1. 使用 [設定 HTTPS]**** 核取方塊，選擇您是否需要 SSL 支援。
1. 請勾選 [啟用 Docker 支援]**** 核取方塊。
1. 選擇容器類型，然後按一下 **"創建**"。 不支援將 Windows 容器作為容器部署到 Azure 應用服務。
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>將容器部署到 Azure

1. 在**方案總管**中以滑鼠右鍵按一下專案，並選擇 [發佈]****。
1. 在發佈目標對話方塊上，選擇**應用服務 Linux**或**應用服務**。 這是將承載 Web 服務器的作業系統。
1. 只能發佈到應用服務，也可以發佈到應用服務和 Azure 容器註冊表 （ACR）。 要在 Azure 容器註冊表 （ACR） 中發佈容器，請選擇為**容器創建新的應用服務**，然後按一下 **"發佈**"。

   ![發佈對話方塊的螢幕截圖](media/deploy-app-service/publish-app-service-linux.PNG)

   要僅在不使用 Azure 容器註冊表的情況下發布到 Azure 應用服務，請選擇 **"創建新**"，然後按一下"**發佈**"。

1. 檢查您是否使用與 Azure 訂閱關聯的帳戶登錄，並選擇唯一名稱、訂閱、資源組、託管計畫和容器註冊表（如果適用）或接受預設值。

   ![發佈設置的螢幕截圖](media/deploy-app-service/publish-app-service-linux2.png)

1. 選擇 **[建立]**。 容器將部署到所選資源組和容器註冊表中的 Azure。 此過程需要一些時間。 完成後，"**發佈"** 選項卡將顯示有關已發佈內容的資訊，包括網站 URL。

   ![發佈選項卡的螢幕截圖](media/deploy-app-service/publish-succeeded.PNG)

1. 按一下網站連結以驗證應用在 Azure 中按預期工作。

   ![Web 應用程式的螢幕截圖](media/deploy-app-service/web-application-running.png)

1. 發佈設定檔將保存與您選擇的所有詳細資訊一起，例如資源組和容器註冊表。

1. 要使用相同的發佈設定檔進行再次部署，請使用 **"發佈"** 按鈕 **、Web 發佈活動**視窗中的 **"發佈**"按鈕，或按右鍵**解決方案資源管理器**中的專案，然後選擇內容功能表上的 **"發佈**"項。

## <a name="view-container-settings"></a>查看容器設置

在[Azure 門戶](https://portal.azure.com)中，可以打開已部署的應用服務。

您可以通過打開 " +*容器設置"* 功能表（使用 Visual Studio 2019 版本 16.4 或更高版本時）查看已部署的應用服務的設置。

![Azure 門戶中容器設置功能表的螢幕截圖](media/deploy-app-service/container-settings-menu.png)

從那裡，您可以查看容器資訊、查看或下載日誌或設置連續部署。 請參閱[Azure 應用服務連續部署 CI/CD](/azure/app-service/containers/app-service-linux-ci-cd)。

## <a name="clean-up-resources"></a>清除資源

要刪除與本教程關聯的所有 Azure 資源，請使用[Azure 門戶](https://portal.azure.com)刪除資源組。 要查找與已發佈的 Web 應用程式關聯的資源組，請選擇 **"查看** > **其他 Windows** > **Web 發佈活動**"，然後選擇齒輪圖示。 "**發佈"** 選項卡將打開，其中包含資源組。

在 Azure 門戶中，選擇 **"資源組**"，選擇資源組以打開其詳細資訊頁。 驗證這是正確的資源組，然後選擇 **"刪除資源組**"，鍵入名稱，然後選擇 **"刪除**"。

## <a name="next-steps"></a>後續步驟

瞭解有關[Azure 應用服務 Linux](/azure/app-service/containers/app-service-linux-intro)的更多。

## <a name="see-also"></a>另請參閱

[部署到 Azure 容器註冊表](hosting-web-apps-in-docker.md)