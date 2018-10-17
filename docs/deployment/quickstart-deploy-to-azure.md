---
title: 發佈至 Azure App Service
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341686"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a> 使用 Visual Studio 將 Web 應用程式發佈至 Azure App Service 

您可以使用**發佈**工具，將 ASP.NET、ASP.NET Core、Node.js 與 .NET Core 應用程式發佈到 Azure App Service 或 Azure App Service Linux (使用容器)。針對 Python 應用程式，請依照 [Python-發佈至 Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) 中所述的步驟執行。

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇**發佈**(或使用**建置** > **發佈**功能表項目)。

    ![在 [方案總管] 中的 [專案] 內容功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇發行")

2. 如果您先前已設定任何發行設定檔，會顯示 [發佈] 窗格，在這個情況下，請選取 [建立新設定檔]。

3. 在 [挑選發佈目標] 對話方塊方塊中，選擇 [App Service]。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-azure.png "選擇 Azure App Service")

4. 選取 [發行]。[建立 App Service] 對話方塊隨即出現。登入您的 Azure 帳戶，如果有需要，預設 App Service 設定會填入欄位。

    ![建立 App Service](../deployment/media/quickstart-publish-settings-app-service.png "建立 Azure App Service")

5. 選取 [建立]。Visual Studio 會將應用程式部署到 Azure App Service ，而且您的 Web 應用程式會在瀏覽器中載入。專案屬性 [發佈] 頁面會顯示網站 URL 與其他詳細資料。

    ![發佈屬性窗格中顯示的設定檔摘要](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>清除資源

在前述步驟中，您可以建立資源群組中的 Azure 資源。 如果您不希望在未來需要這些資源，您可以藉由刪除資源群組中刪除它們。
從 Azure 入口網站左側功能表中，選取**資源群組**，然後選取**myResourceGroup**。
在資源群組頁面上，確定列出的資源是您想要刪除的項目。
選取 [刪除]，在文字方塊中輸入 **myResourceGroup**，然後選取 [刪除]。

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔以部署到 Azure。您也可以透過從 Azure App Service 匯入發行設定來設定發行設定檔。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 Azure](tutorial-import-publish-settings-azure.md)
