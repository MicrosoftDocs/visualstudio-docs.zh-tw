---
title: 發行至網站
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1236c3057cd209bd5c7c81304a2168704927c506
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127940"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>使用 Visual Studio 將 Web 應用程式發行至網站

您可以使用 [發行] 工具，從 Visual Studio 將 ASP.NET、ASP.NET Core、.NET Core 及 Python 應用程式發行至網站。 針對 Node.js，支援這些步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> 如果您需要將 Windows 桌面應用程式發行至網路檔案共用，請參閱[使用 ClickOnce 部署桌面應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# 或 Visual Basic)。 針對C++/cli，請參閱[使用 ClickOnce 部署原生應用程式](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)，若為C++C/，請參閱[使用安裝專案部署原生應用](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)程式。

## <a name="publish-to-a-web-site"></a>發行至網站

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![[方案總管] 中專案操作功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您之前已設定任何發行設定檔，[發行] 窗格會隨即出現。 選取 [建立新設定檔]。

1. 在 [挑選發行目標] 對話方塊中，選擇 [IIS、FTP 等等]。

    ![選擇 [IIS、FTP 等等]](../deployment/media/quickstart-publish-iis-ftp.png "選擇 [IIS、FTP 等等]")

1. 選取 [發行]。 設定檔發行設定對話方塊隨即開啟。

    ![選擇資料夾](../deployment/media/quickstart-publish-settings-web.png "選擇資料夾")

1. 在 [發行方法] 欄位中，選擇一種方法，例如 [Web Deploy] 或 [FTP]。 您看到之設定接下來會對應至您的發行方法。 Web Deploy 可簡化將 Web 應用程式和網站部署到 IIS 伺服器的作業，而且必須安裝為伺服器上的應用程式。 請使用 [Web platform installer](https://www.microsoft.com/web/downloads/platform.aspx) 進行安裝。

1. 設定發行方法的必要設定，然後選取 [驗證連線]。 如果伺服器或目標可供使用且您的設定正確，則會顯示一則訊息指出已驗證連線，且您已經準備好發行。

    ![驗證您的連線](../deployment/media/quickstart-publish-web-deploy.png "驗證您的連線")

1. 選取 [設定] 設定其他部署設定，例如是否要部署 [偵錯] 或 [發行] 組態，然後選取 [儲存]。 如果您要遠端偵錯，則需要 [偵錯] 組態。

1. 若要發行，請選取 [發行]。 [輸出] 視窗會顯示部署進度和結果。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔。 您也可以匯入發行設定來設定發行設定檔。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 IIS](tutorial-import-publish-settings-iis.md)
