---
title: 發佈至 Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 4bbff0c2d149afddc355afe5f6c93e9d0aea54c0
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806906"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>使用 Visual Studio 將 Web 應用程式發行至 Azure App Service

針對 ASP.NET、ASP.NET Core、Node.js 和 .NET Core 應用程式，使用下列其中一個方法發行至 Azure App Service 或 Azure App Service Linux (使用容器)。

* 針對連續 (或自動) 部署應用程式，使用 Azure DevOps 與 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)。

* 針對一次 (或手動) 部署應用程式，使用 Visual Studio 中的 [發行] 工具將 ASP.NET、ASP.NET Core、Node.js 和 .NET Core 應用程式部署至 Azure App Service 或 App Service for Linux (使用容器)。 針對 Python 應用程式，請遵循[發行至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) 的步驟。

本文說明如何使用 [發行] 工具來進行一次部署。

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![[專案] 內容功能表上的 [發佈] 命令方案總管](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您之前已設定任何發行設定檔，[發行] 窗格隨即出現；在此情況下，請選取 [建立新設定檔]。

1. 在 [挑選發行目標] 對話方塊中，選擇 [App Service]。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-azure.png "選擇 Azure App Service")

1. 選取 [發行]。 [建立 App Service] 對話方塊隨即出現。 如有必要，請使用您的 Azure 帳戶登入，接著預設 App Service 設定會填入欄位。

    ![建立 App Service](../deployment/media/quickstart-publish-settings-app-service.png "建立 Azure App Service")

1. 選取 [建立]。 Visual Studio 會將應用程式部署至 Azure App Service，並在瀏覽器中載入 Web 應用程式。 專案屬性 [發行] 窗格會顯示網站 URL 和其他詳細資料。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>清除資源

在上述步驟中，您已建立資源群組中的 Azure 資源。 如果您預期未來不需要這些資源，則可以藉由刪除資源群組予以刪除。
從 Azure 入口網站左側功能表中，選取 [資源群組]，然後選取 **myResourceGroup**。
在 [資源群組] 頁面上，確定所列出資源是您想要刪除的資源。
選取 [刪除]，在文字方塊中鍵入，然後選取 [刪除]。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔，以部署至 Azure。 您也可以從 Azure App Service 匯入發行設定來設定發行設定檔。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 Azure](tutorial-import-publish-settings-azure.md)
