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
ms.openlocfilehash: 461b99261eb88d5267b062cb5d471f1b6ed4ee60
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248034"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>使用 Visual Studio 將 Web 應用程式發行至 Azure App Service

針對 ASP.NET、ASP.NET Core、Node.js 和 .NET Core 應用程式，使用下列其中一個方法發行至 Azure App Service 或 Azure App Service Linux (使用容器)。

* 針對連續 (或自動) 部署應用程式，使用 Azure DevOps 與 [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops)。

* 針對一次 (或手動) 部署應用程式，使用 Visual Studio 中的 [發行]**** 工具將 ASP.NET、ASP.NET Core、Node.js 和 .NET Core 應用程式部署至 Azure App Service 或 App Service for Linux (使用容器)。 針對 Python 應用程式，請遵循[發行至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) 的步驟。

本文說明如何使用 [發行]**** 工具來進行一次部署。

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>發佈至 Windows 上的 Azure App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行]**** (或使用 [建置]**** > [發行]**** 功能表項目)。

    ![[專案] 內容功能表上的 [發佈] 命令方案總管](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 在 [ **發佈** ] 對話方塊中，選取 [ **Azure**]。

    ![選擇發行目標](../deployment/media/quickstart-publish-azure-new.png)

1. 選取 [ **Azure App Service (Windows) ** **] 和 [下一步]**。

    ![選擇 Linux 上的 Azure App Service](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. 如有需要，請使用您的 Azure 帳戶登入。 選取 [**建立新的 Azure App Service ...** ]

    ![用來建立新實例 Azure App Service 的連結](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. 在 [ **建立 Azure App Service (Windows) ** ] 對話方塊中，會填入 [ **應用程式名稱**]、[ **資源群組**] 和 [ **App Service 計畫** ] 專案欄位。 您可以保留這些名稱，或變更它們。 準備好時，請選取 [ **建立**]。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. 在 [ **發行** ] 對話方塊中，已自動選取新建立的實例。 準備好時，按一下 **[完成]**。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-windows-select-instance.png)

1. 選取 [發佈]。 Visual Studio 會將應用程式部署至 Azure App Service，並在瀏覽器中載入 Web 應用程式。 專案屬性 [發行]**** 窗格會顯示網站 URL 和其他詳細資料。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>清除資源

在前述步驟中，您在資源群組中建立了 Azure 資源。 如果您認為未來不需要這些資源，可以用刪除資源群組的方式將它們刪除。
從 Azure 入口網站的左側功能表中，依序選取 [資源群組]**** 和 [myResourceGroup]****。
在 [資源群組] 頁面上，確定所列出的資源是您想要刪除的項目。
選取 [刪除]****，在文字方塊中輸入 **myResourceGroup**，然後再選取 [刪除]****。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔，以部署至 Azure。 您也可以從 Azure App Service 匯入發行設定來設定發行設定檔。

> [!div class="nextstepaction"]
> [匯入發行設定並部署至 Azure](tutorial-import-publish-settings-azure.md)
