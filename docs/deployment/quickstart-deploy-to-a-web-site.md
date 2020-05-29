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
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173673"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>使用 Visual Studio 將 Web 應用程式發行至網站

您可以使用 [發行]**** 工具，從 Visual Studio 將 ASP.NET、ASP.NET Core、.NET Core 及 Python 應用程式發行至網站。 針對 Node.js，支援這些步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> 如果您需要將 Windows 桌面應用程式發行至網路檔案共用，請參閱[使用 ClickOnce 部署桌面應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# 或 Visual Basic)。 針對 C++/CLR，請參閱[使用 ClickOnce 部署原生應用程式](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)，針對 C/C++，請參閱[使用安裝專案部署原生應用程式](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)。

## <a name="publish-to-a-web-site"></a>發行至網站

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行]**** (或使用 [建置]**** > [發行]**** 功能表項目)。

    ![[專案] 內容功能表上的 [發佈] 命令方案總管](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您之前已設定任何發行設定檔，[發行]**** 窗格會隨即出現。 選取 [建立新設定檔]****。

1. 在 [**發行**] 對話方塊中，選擇 [**網頁伺服器（IIS）**]。

    ![選擇發行目標](../deployment/media/quickstart-publish-iis.png "選擇 [IIS、FTP 等等]。")

1. 選擇 [ **Web Deploy** ] 作為部署方法。 Web Deploy 可簡化將 Web 應用程式和網站部署到 IIS 伺服器的作業，而且必須安裝為伺服器上的應用程式。 請使用 [Web platform installer](https://www.microsoft.com/web/downloads/platform.aspx) 進行安裝。

    ![選擇部署方法](../deployment/media/quickstart-publish-iis-web-deploy.png "選擇 [IIS、FTP 等等]。")

1. 設定 publish 方法所需的設定，然後選取 **[完成]**。 

    ![Web Deploy 連線詳細資料](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. 若要發佈，請在 [摘要] 頁面中選取 [**發佈**]。 [輸出] 視窗會顯示部署進度和結果。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔。 您也可以匯入發行設定來設定發行設定檔。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 IIS](tutorial-import-publish-settings-iis.md)
