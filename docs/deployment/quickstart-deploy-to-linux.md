---
title: 發佈至 Linux 上的 App Service
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 9f79cef595b3a58426b596fc1019c59b801a02d5
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252358"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>將 ASP.NET Core 應用程式發行至 App Service 在 Linux 上使用 Visual Studio

您可以使用**發佈**發佈至 Azure App Service，Linux 上的 ASP.NET Core 應用程式的工具。

在 Linux 上使用的部署至 App Service**發佈**工具需要 Visual Studio 2017 15.7 版。

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>發佈至 Linux 上的 App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇**發佈**(或使用**建置** > **發佈**功能表項目)。

    ![在 [方案總管] 中的 [專案] 內容功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇發行")

1. 如果您先前已設定任何發行的設定檔**發佈**窗格出現時，在哪一個案例中，選取**建立新的設定檔**。

1. 在 **挑選發行目標**對話方塊方塊中，選擇**App Service Linux**。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-linux.png "選擇 Azure App Service")

1. 選取 [發行]。 **建立 App Service**  對話方塊隨即出現。 登入您 Azure 帳戶，如果有需要，則預設 app service 設定填入的欄位。

    ![建立 App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "建立 Azure App Service")

1. 選取 [建立]。 Visual Studio 部署至 Azure App Service 的應用程式和 web 應用程式載入瀏覽器中。 專案屬性**發佈** 窗格會顯示網站 URL 和其他詳細資料。

    ![發佈屬性窗格中顯示的設定檔摘要](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何在 Linux 上建立發行設定檔部署至 App Service 使用 Visual Studio。 您可能想要使用 Azure 的 Linux 發佈的詳細資訊。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
