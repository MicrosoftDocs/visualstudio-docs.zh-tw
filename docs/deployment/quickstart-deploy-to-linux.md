---
title: 發行至 Linux 上的 App Service
description: 瞭解使用容器將 ASP.NET Core 應用程式發佈至 Azure App Service Linux 的方法，包括連續和一次性的選項。
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 27002d9360d36330249167b2cc8b75b7cd832135
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815629"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>使用 Visual Studio 將 ASP.NET Core 應用程式發行至 Linux 上的 App Service

從 Visual Studio 2017 版本 15.7 開始，您可以使用下列其中一個方法將 ASP.NET Core 應用程式發行至 Azure App Service Linux (使用容器)。

* 針對連續 (或自動) 部署應用程式，使用 Azure DevOps 與 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)。

* 針對一次 (或手動) 部署應用程式，使用 Visual Studio 中的 [發行] 工具將 ASP.NET Core 應用程式發行至 App Service for Linux (使用容器)。

本文說明如何使用 [發行] 工具來進行一次部署。

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>發佈至 Linux 上的 Azure App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![方案總管的專案內容功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您先前已設定任何發行設定檔，[ **發行** ] 視窗隨即出現。 選取 [ **新增**]。

1. 在 [ **發佈** ] 視窗中，選取 [ **Azure**]。

    ![選擇發佈目標](../deployment/media/quickstart-publish-azure-new.png)

1. 選取 **Azure App Service (Linux)** 和 **下一步]**。

    ![選擇 Linux 上的 Azure App Service](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. 如有必要，請使用您的 Azure 帳戶登入。 選取 [ **建立新的 Azure App Service ...**

    ![Azure App Service 建立新實例的連結](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. 在 [ **建立 Azure App Service (Linux)** ] 對話方塊中，會填入 [ **應用程式名稱**]、[ **資源群組**] 和 [ **App Service 方案** ] 專案欄位。 您可以保留這些名稱，或變更它們。 準備好時，請選取 [ **建立**]。

    ![[建立 Azure App Service (Linux) ] 對話方塊的螢幕擷取畫面，其中已填入名稱、訂用帳戶、資源群組和主控方案欄位。](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. 在 [ **發行** ] 對話方塊中，會自動選取新建立的實例。 準備好時，按一下 **[完成]**。

    ![[發行] 對話方塊的螢幕擷取畫面，其中已選取新建立的 MyASpCoreWebAppOnAzure 服務作為發佈 App Service。](../deployment/media/quickstart-publish-linux-select-instance.png)

1. 選取 [發佈]  。 Visual Studio 會將應用程式部署至 Azure App Service，並在瀏覽器中載入 Web 應用程式。 專案屬性 [發行] 窗格會顯示網站 URL 和其他詳細資料。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>清除資源

在前述步驟中，您在資源群組中建立了 Azure 資源。 如果您認為未來不需要這些資源，可以用刪除資源群組的方式將它們刪除。
從 Azure 入口網站的左側功能表中，依序選取 [資源群組] 和 [myResourceGroup]。
在 [資源群組] 頁面上，確定所列出的資源是您想要刪除的項目。
選取 [刪除]，在文字方塊中輸入 **myResourceGroup**，然後再選取 [刪除]。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔，以部署至 linux 上的 App Service。 您可能需要使用 Azure 發行至 Linux 的詳細資訊。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)