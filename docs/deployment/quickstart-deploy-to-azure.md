---
title: "發行至 Azure 的應用程式服務-Visual Studio |Microsoft 文件"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: azure
ms.openlocfilehash: 52da1a2e618d9ececa1c8fd0d90a86e651cd7fde
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>將 ASP.NET 或 ASP.NET Core 應用程式發行至使用 Visual Studio 的 Azure 應用程式服務

您可以使用**發行**工具，以 ASP.NET、 ASP.NET Core、 Python、 Node.js 和.NET Core 應用程式發行至 Azure App Service。

如果您沒有 Azure 帳戶，您可以[這裡進行註冊](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

1. 在下**Visual C#**或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**（僅限 C#) 或**ASP.NET Core Web 應用程式**，然後按一下 **確定**。

1. 選擇**MVC**，請確定**非驗證**已選取，然後按一下**確定**。

1. 輸入的名稱，例如**MyWebApp**按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置 > 建置方案**建置專案。

## <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。

    ![選擇發行](../deployment/media/quickstart-publish-aspnet.png "選擇發行")

1. 在**發行** 窗格中，選擇**Microsoft Azure App Service**。

    ![選擇 Azure App Service](../deployment/media/quickstart-publish-azure.png "選擇 Azure App Service")

1. 按一下 [發行] 。

    **建立 App Service**  對話方塊隨即出現。

    ![建立 App Service](../deployment/media/quickstart-publish-settings-app-service.png "建立 Azure App Service")
    
1. 如果您未登入 Visual Studio，登入，並預設應用程式服務設定然後填入欄位。

    設定檔發佈的設定 對話方塊隨即開啟。

    ![選擇資料夾](../deployment/media/quickstart-publish-settings-web.png "選擇資料夾")

    您可以在這個對話方塊中，選取您要使用的訂用帳戶、 選取或建立 Azure 資源群組和其他內容。

1. 按一下 [建立] 。

    Visual Studio 會將應用程式部署到您的 Azure 應用程式服務和 web 應用程式載入您的瀏覽器中。

    中的摘要**發行** 窗格中，您可以看到新的 Azure App Service 網站 URL。

## <a name="next-steps"></a>後續步驟

- [ASP.NET Core 應用程式部署至 Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [使用 Git 將 ASP.NET Core 持續部署到 Azure](/aspnet/core/publishing/azure-continuous-deployment)
