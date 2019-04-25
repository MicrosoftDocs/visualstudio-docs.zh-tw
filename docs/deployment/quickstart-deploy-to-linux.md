---
title: 發行至 Linux 上的 App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 12d1df3874388f0c113600e20ca2dbd080d15d10
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899112"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>使用 Visual Studio 將 ASP.NET Core 應用程式發行至 Linux 上的 App Service

從 Visual Studio 2017 版本 15.7 開始，您可以使用下列其中一個方法將 ASP.NET Core 應用程式發行至 Azure App Service Linux (使用容器)。

* 針對連續 (或自動) 部署應用程式，使用 Azure DevOps 與 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops)。

* 針對一次 (或手動) 部署應用程式，使用 Visual Studio 中的 [發行] 工具將 ASP.NET Core 應用程式發行至 App Service for Linux (使用容器)。

本文說明如何使用 [發行] 工具來進行一次部署。

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>發行至 Linux 上的 App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![[方案總管] 中專案操作功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您之前已設定任何發行設定檔，[發行] 窗格隨即出現；在此情況下，請選取 [建立新設定檔]。

1. 在 [挑選發行目標] 對話方塊中，選擇 [App Service Linux]。

    ![選擇 [Azure App Service]](../deployment/media/quickstart-publish-linux.png "選擇 [Azure App Service]")

1. 選取 [發行]。 [建立 App Service] 對話方塊隨即出現。 如有必要，請使用您的 Azure 帳戶登入，接著預設 App Service 設定會填入欄位。

    ![建立 App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "建立 Azure App Service")

1. 選取 [建立]。 Visual Studio 會將應用程式部署至 Azure App Service，並在瀏覽器中載入 Web 應用程式。 專案屬性 [發行] 窗格會顯示網站 URL 和其他詳細資料。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>清除資源

在上述步驟中，您已建立資源群組中的 Azure 資源。 如果您預期未來不需要這些資源，則可以藉由刪除資源群組予以刪除。
從 Azure 入口網站左側功能表中，選取 [資源群組]，然後選取 **myResourceGroup**。
在 [資源群組] 頁面上，確定所列出資源是您想要刪除的資源。
選取 [刪除]，在文字方塊中鍵入 ，然後選取 [刪除]。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔，以部署至 linux 上的 App Service。 您可能需要使用 Azure 發行至 Linux 的詳細資訊。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
