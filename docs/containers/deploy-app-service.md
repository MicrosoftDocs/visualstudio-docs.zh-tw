---
title: 將 ASP.NET Core 容器部署至 Azure App Service
description: 瞭解如何使用 Visual Studio 容器工具將 Docker 容器中的 ASP.NET Core web 應用程式部署至 Azure App Service
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 02/21/2021
ms.author: ghogen
ms.openlocfilehash: f9a4f26227d2cd3bd065fab88ba294f7341ea4ed
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684297"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>使用 Visual Studio 將 ASP.NET Core 容器部署至 Azure App Service

本教學課程會逐步引導您使用 Visual Studio，將容器化 ASP.NET Core web 應用程式發佈至 [Azure App Service](/azure/app-service)。 Azure App Service 是 Azure 中託管的單一容器 web 應用程式的適當服務。

如果您沒有 Azure 訂用帳戶，請在開始前建立[免費帳戶](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs)。

## <a name="prerequisites"></a>必要條件

若要完成本教學課程：

::: moniker range="vs-2017"
- 安裝包含 "ASP.NET 和 Web 開發" 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 最新版本
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，其中包含 *ASP.NET 和 Web 部署* 工作負載。
::: moniker-end
- 安裝 [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>建立 ASP.NET Core Web 應用程式

下列步驟會逐步引導您建立將在本教學課程中使用的基本 ASP.NET Core 應用程式。

::: moniker range="vs-2017"
1. 從 Visual Studio 功能表中，選取 [檔案] > [新增] > [專案]。
2. 在 [新增專案] 對話方塊的 [範本] 區段下，選取 [Visual C#] > [Web]。
3. 選取 **ASP.NET Core Web 應用程式**。
4. 指定新應用程式的名稱 (或使用預設值)，然後選取 [確定] 。
5. 選取 [ **Web 應用程式**]。
6. 請勾選 [啟用 Docker 支援] 核取方塊。
7. 選取 **Linux** 容器類型，然後按一下 **[確定]**。 不支援 Windows 容器以容器的形式部署至 Azure App Service。
::: moniker-end
::: moniker range=">= vs-2019"
1. 從 Visual Studio 的開始視窗中，選擇 [建立新專案]。
1. 選擇 [ **ASP.NET Core Web 應用程式**]，然後選擇 **[下一步]**。
1. 為新的應用程式命名 (或採用預設) ，然後選擇 **[下一步]**。
1. 選擇您想要設為目標的 .NET 版本。 如果您不確定，請選擇 (LTS) 版本的長期支援。
1. 使用 [設定 HTTPS] 核取方塊，選擇您是否需要 SSL 支援。
1. 請勾選 [啟用 Docker 支援] 核取方塊。
1. 選取容器類型，然後按一下 [ **建立**]。
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>將容器部署至 Azure

::: moniker range="vs-2017"

1. 在 **方案總管** 中以滑鼠右鍵按一下專案，並選擇 [發佈]。
1. 在 [發佈目標] 對話方塊中，選擇 [ **App Service Linux** ] 或 [ **app service**]。 這是將裝載 web 伺服器的作業系統。
1. 您只可以發佈至 App Service，也可以發佈至 App Service 和 Azure Container Registry (ACR) 。 若要在 Azure Container Registry (ACR) 中發佈容器，請選擇 [ **建立容器的新 App Service**]，然後按一下 [ **發佈**]。

   ![[發佈] 對話方塊的螢幕擷取畫面](media/deploy-app-service/publish-app-service-linux-1.png)

   若只要發佈到 Azure App Service，而不使用 Azure Container Registry，請選擇 [ **建立新** 的]，然後按一下 [ **發佈**]。

1. 確認您已使用與 Azure 訂用帳戶相關聯的帳戶登入，然後選擇唯一的名稱、訂用帳戶、資源群組、主控方案和容器登錄 (如果適用) ，或接受預設值。

   ![發佈設定的螢幕擷取畫面](media/deploy-app-service/publish-app-service-linux-2.png)

1. 選擇 **[建立]** 。 您的容器會部署到您選取的資源群組和容器登錄中的 Azure。 此程式需要一些時間。 完成時，[ **發佈** ] 索引標籤會顯示已發佈內容的相關資訊，包括網站 URL。

   ![[發佈] 索引標籤的螢幕擷取畫面](media/deploy-app-service/publish-succeeded.PNG)

1. 按一下 [網站] 連結，以確認您的應用程式在 Azure 中如預期般運作。

   ![Web 應用程式的螢幕擷取畫面](media/deploy-app-service/web-application-running.png)

1. 發行設定檔會與您選取的所有詳細資料（例如資源群組和容器登錄）一起儲存。

1. 若要使用相同的發行設定檔再次部署，請使用 [**發行**] 按鈕、在 [ **Web 發行活動**] 視窗上的 [**發行**] 按鈕，或在 [**方案瀏覽器**] 中的專案上按一下滑鼠右鍵，然後選擇內容功能表上的 [**發行**] 專案。
:::moniker-end
:::moniker range=">=vs-2019"
1. 在 **方案總管** 中以滑鼠右鍵按一下專案，並選擇 [發佈]。
1. 在 [ **發行** ] 對話方塊中，選擇 [ **Azure** ] 目標。

   ![[發佈嚮導] 的螢幕擷取畫面](media/deploy-app-service/publish-choices.png)

1. 在 [ **特定目標** ] 索引標籤上，根據您的容器類型選擇適當的部署目標，例如 **App service (Windows)** 或 **app service (Linux)**。

   ![[發佈嚮導] 中特定目標索引標籤的螢幕擷取畫面](media/deploy-app-service/publish-app-service-windows.png)

1. 如果您未使用您想要使用的訂用帳戶登入正確的 Azure 帳戶，請使用 [ **發佈** ] 視窗左上角的按鈕登入。

1. 您可以使用現有的 app service，或按一下 [ **建立新的 Azure App service** ] 連結來建立新的應用程式服務。 展開樹狀檢視中的資源群組，以在 treeview 中尋找現有的 app service，或將 **View** 設定變更為 **資源類型** ，以依類型排序。

   ![顯示選擇 App Service 的螢幕擷取畫面](media/deploy-app-service/publish-app-service-windows2.png)

1. 如果您建立新的資源群組，將會在 Azure 中產生資源群組和應用程式服務。 您可以視需要變更名稱，前提是它們是唯一的。

   ![顯示建立 App Service 的螢幕擷取畫面](media/deploy-app-service/publish-app-service-windows3.png)

1. 您可以接受預設的主控方案，或在 Azure 入口網站中立即變更主控方案。 預設值是 `S1` 在其中一個支援的區域 (small) 。 若要建立主控方案，請選擇 [**主控方案**] 下拉式清單旁的 [**新增**]。 [ **主控方案** ] 視窗隨即出現。

   ![顯示主控方案選項的螢幕擷取畫面](media/deploy-app-service/hosting-plan.png)

   您可以在 [Azure App Service 方案總覽](/azure/app-service/overview-hosting-plans)中查看這些選項的詳細資料。

1. 當您完成選取或建立這些資源之後，請選擇 **[完成]**。 您的容器會部署至您所選取之資源群組和 app service 中的 Azure。 此程式需要一些時間。 完成時，[ **發佈** ] 索引標籤會顯示已發佈內容的相關資訊，包括網站 URL。

   ![[發佈] 索引標籤的螢幕擷取畫面](media/deploy-app-service/publish-succeeded-windows.png)

1. 按一下 [網站] 連結，以確認您的應用程式在 Azure 中如預期般運作。

   ![Web 應用程式的螢幕擷取畫面](media/deploy-app-service/web-application-running2.png)

1. 發行設定檔會隨您選取的所有詳細資料（例如資源群組和 app service）儲存。

1. 若要使用相同的發行設定檔再次部署，請使用 [**發行**] 按鈕、在 [ **Web 發行活動**] 視窗上的 [**發行**] 按鈕，或在 [**方案瀏覽器**] 中的專案上按一下滑鼠右鍵，然後選擇內容功能表上的 [**發行**] 專案。
:::moniker-end

## <a name="view-container-settings"></a>查看容器設定

在 [Azure 入口網站](https://portal.azure.com)中，您可以開啟已部署的 App Service。

當您使用 Visual Studio 2019 16.4 版或更新版本的) 時，可以開啟 [ **容器設定** ] 功能表 (，以查看已部署之 App Service 的設定。

![Azure 入口網站中 [容器設定] 功能表的螢幕擷取畫面](media/deploy-app-service/container-settings-menu.png)

從該處，您可以查看容器資訊、查看或下載記錄，或設定持續部署。 請參閱 [Azure App Service 持續部署 CI/CD](/azure/app-service/containers/app-service-linux-ci-cd)。

## <a name="clean-up-resources"></a>清除資源

若要移除與本教學課程相關聯的所有 Azure 資源，請使用 [Azure 入口網站](https://portal.azure.com)刪除資源群組。 若要尋找與已發佈之 web 應用程式相關聯的資源群組，請選擇 [ **View**  >  **Other Windows**  >  **web Publish 活動**]，然後選擇齒輪圖示。 [ **發行** ] 索引標籤隨即開啟，其中包含資源群組。

在 Azure 入口網站中，選擇 [ **資源群組**]，選取資源群組以開啟其詳細資料頁面。 確認這是正確的資源群組，然後選擇 [ **移除資源群組**]，輸入名稱，然後選擇 [ **刪除**]。

## <a name="next-steps"></a>下一步

深入瞭解 [Azure App Service](/azure/app-service/overview)。

## <a name="see-also"></a>另請參閱

[部署至 Azure Container Registry](hosting-web-apps-in-docker.md)