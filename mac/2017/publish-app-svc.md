---
title: 發佈至 Azure App Service
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 49a8dfb3625ebda01caf0d0fa806b197c1bdaefb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722993"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 將 Web 應用程式發佈到 Azure App Service

您可以使用 [發佈] 工具，將 ASP.NET Core 應用程式發佈到 Azure App Service。

## <a name="prerequisites"></a>Prerequisites

- 已安裝 [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) 並啟用 ASP.NET Core。
- Azure 訂用帳戶。 如果您還沒有訂用帳戶，可以[免費註冊](https://azure.microsoft.com/free/dotnet/)，其中包含 30 天美金 $200 元的點數及 12 個月熱門免費服務。
- ASP.NET Core 專案。 如果您還沒有專案，可以[建立新的專案](./create-new-projects.md?view=vsmac-2017&preserve-view=true)。

## <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

 1. 在 Solution Pad 中，以滑鼠右鍵按一下專案，然後選擇 [發佈]。

    ![[發佈] 操作功能表](media/publish-context-menu.png)

 2. 如果您之前已將此專案發佈到 Azure App Service，您將會在功能表中看到發行設定檔。 選取該發行設定檔即可啟動發佈程序。

 3. 若是第一次將此專案發佈到 App Service，請選取 [發佈到 Azure]

    ![[發佈到 App Service] 操作功能表](media/publish-to-azure-context-menu.png)

 4. [發佈到 Azure App Service] 對話方塊會隨即出現，並顯示任何現有的 App Service。 若要發佈到現有的 App Service，請在清單中選取 App Service，然後按一下 [發佈]。

    ![[發佈到 Azure App Service] 對話方塊](media/publish-to-app-service-dialog.png)

 5. 若要建立新的 App Service，請按一下 [新增] 按鈕。

    ![[發佈到 App Service] 對話方塊](media/publish-to-app-service-dialog-new-selected.png)

 6. [新增 App Service] 對話方塊會隨即出現。 在此對話方塊中，您可以設定新 App Service 的設定。

    ![[新增 App Service] 對話方塊](media/publish-new-app-service.png)

    您可以在這裡考慮自訂一些選項。 App Service 的名稱會預設為專案名稱。 如果此名稱無法使用，則會在輸入欄位右邊顯示警告標誌。 App Service 名稱會用於您網站的 URL，因此名稱必須有效才能用於 URL。

    您可以使用 [訂用帳戶] 下拉式清單，變更要與 App Service 建立關聯的訂用帳戶。

    您可以使用下拉式清單選取現有的 **資源群組**，也可以使用 **+** 按鈕建立新的資源群組。

    針對 App Service 方案，請選取現有的方案，或選取 [自訂] 選項按鈕來建立新的方案。

    若要建立新 App Service 並將您的專案發佈到其中，請按一下 [建立]。

    按一下 [建立] 之後，[新增 App Service] 對話方塊會隨即關閉，且您應該會看到下列訊息，指出已開始建立 App Service。

      ![建立 App Service 訊息](media/publish-create-app-service-message.png)

    按一下 [確定] 之後，訊息會隨即關閉，且您可以繼續進行專案。 您可以使用 IDE 頂端之狀態列來監看發佈程序的狀態。 當您的 Web 應用程式成功發佈之後，即會以您的預設瀏覽器開啟網站。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]