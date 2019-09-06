---
title: 將 ASP.NET Core Docker 容器部署至 Azure App Service |Microsoft Docs
description: 瞭解如何使用 Visual Studio 容器工具將 ASP.NET Core web 應用程式部署至 Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 03/08/2019
ms.author: ghogen
ms.openlocfilehash: 9431046c57851e31a3711b4785f9cce45acab45f
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312206"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>使用 Visual Studio 將 ASP.NET Core 容器部署至 Azure App Service

本教學課程將逐步引導您使用 Visual Studio，將容器化的 ASP.NET Core web 應用程式發佈至[Azure App Service](/azure/app-service)。 針對 Azure 中裝載的單一容器 web 應用程式，Azure App Service 是適當的服務。

如果您沒有 Azure 訂用帳戶，請在開始前建立 [免費帳戶](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) 。

## <a name="prerequisites"></a>必要條件

完成本教學課程：

::: moniker range="vs-2017"
- 安裝包含 "ASP.NET 和 Web 開發" 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 最新版本
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)搭配*ASP.NET 和 網頁程式開發*工作負載。
::: moniker-end
- 安裝[Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>建立 ASP.NET Core Web 應用程式

下列步驟會逐步引導您建立將在本教學課程中使用的基本 ASP.NET Core 應用程式。

::: moniker range="vs-2017"
1. 從 Visual Studio 功能表中，選取 [檔案] > [新增] > [專案]。
2. 在 [新增專案] 對話方塊的 [範本] 區段下，選取 [Visual C#] > [Web]。
3. 選取 [ASP.NET Core Web 應用程式]。
4. 指定新應用程式的名稱 (或使用預設值)，然後選取 [確定]。
5. 選取 [Web 應用程式]。
6. 請勾選 [啟用 Docker 支援] 核取方塊。
7. 選取 [ **Linux** ] 容器類型，然後按一下 **[確定]** 。 Windows 容器不支援以容器的形式部署至 Azure App Service。
::: moniker-end
::: moniker range=">= vs-2019"
1. 從 Visual Studio 的開始視窗中，選擇 [建立新專案]。
1. 依序選擇 [ASP.NET Core Web 應用程式] 和 [下一步]。
1. 指定新應用程式的名稱 (或使用預設)，然後選擇 [建立]。
1. 選擇 [Web 應用程式]。
1. 使用 [設定 HTTPS] 核取方塊，選擇您是否需要 SSL 支援。
1. 請勾選 [啟用 Docker 支援] 核取方塊。
1. 選取 [ **Linux** ] 容器類型，然後按一下 [**建立**]。 Windows 容器不支援以容器的形式部署至 Azure App Service。
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>將容器部署至 Azure

1. 在**方案總管**中以滑鼠右鍵按一下專案，並選擇 [發佈]。
1. 在 [發行目標] 對話方塊中，選擇 [ **App Service Linux**]。
1. 您只能發行至 App Service，或者可以同時發行至 App Service 和 Azure Container Registry （ACR）。 若要在 Azure Container Registry （ACR）中發佈容器，請選擇 [**建立容器的新 App Service**]，然後按一下 [**發佈**]。

   ![[發行] 對話方塊的螢幕擷取畫面](media/deploy-app-service/publish-app-service-linux.PNG)

   若只要發佈至 Azure App Service，而不使用 Azure Container Registry，**請選擇 [新建]** ，然後按一下 [**發佈**]。

1. 請確認您已使用與您的 Azure 訂用帳戶相關聯的帳戶登入，然後選擇唯一的名稱、訂用帳戶、資源群組、主控方案和容器登錄（如果適用），或接受預設值。

   ![發佈設定的螢幕擷取畫面](media/deploy-app-service/publish-app-service-linux2.png)

1. 選擇 [**建立**]。 您的容器會部署至您選取的資源群組和容器登錄中的 Azure。 此程式需要一些時間。 完成時，[**發佈**] 索引標籤會顯示已發行內容的相關資訊，包括網站 URL。

   ![[發佈] 索引標籤的螢幕擷取畫面](media/deploy-app-service/publish-succeeded.PNG)

1. 按一下 [網站] 連結，以確認您的應用程式在 Azure 中如預期般運作。

   ![Web 應用程式的螢幕擷取畫面](media/deploy-app-service/web-application-running.png)

1. 發行設定檔會與您選取的所有詳細資料一起儲存，例如資源群組和容器登錄。
1. 若要使用相同的發行設定檔再次部署，請使用 [**發佈**] 按鈕、[ **Web 發行活動**] 視窗上的 [**發行**] 按鈕，或以滑鼠右鍵按一下**方案總管**中的專案，然後選擇 [**發行**] 專案內容功能表。

## <a name="clean-up-resources"></a>清除資源

若要移除與本教學課程相關聯的所有 Azure 資源，請使用[Azure 入口網站](https://portal.azure.com)刪除資源群組。 若要尋找與已發佈 web 應用程式相關聯的資源群組，請選擇 [**查看** > **其他 Windows**  >  **web 發行活動**]，然後選擇齒輪圖示。 [**發佈**] 索引標籤隨即開啟，其中包含資源群組。

在 Azure 入口網站中，選擇 **資源群組**，選取資源群組以開啟其詳細資料頁面。 確認這是正確的資源群組，然後選擇 [**移除資源群組**]，輸入名稱，然後選擇 [**刪除**]。

## <a name="next-steps"></a>後續步驟

使用[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)設定持續整合與傳遞（CI/CD）。

## <a name="see-also"></a>另請參閱

[部署至 Azure Container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md)