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
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341744"
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

## <a name="clean-up-resources"></a>清除資源

在前述步驟中，您可以建立資源群組中的 Azure 資源。 如果您不希望在未來需要這些資源，您可以藉由刪除資源群組中刪除它們。
從 Azure 入口網站左側功能表中，選取**資源群組**，然後選取**myResourceGroup**。
在資源群組頁面上，確定列出的資源是您想要刪除的項目。
選取 **刪除**，型別**myResourceGroup**文字方塊中，然後選取**刪除**。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何在 Linux 上建立發行設定檔部署至 App Service 使用 Visual Studio。 您可能想要使用 Azure 的 Linux 發佈的詳細資訊。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
