---
title: 發行至網站
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
- multiple
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077499"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>將 Web 應用程式發行至網站，使用 Visual Studio

您可以使用**發佈**工具，以從 Visual Studio 將 ASP.NET、 ASP.NET Core、.NET Core 及 Python 應用程式發行至網站。 適用於 Node.js，支援步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>發行至網站

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇**發佈**(或使用**建置** > **發佈**功能表項目)。

    ![在 [方案總管] 中的 [專案] 內容功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇發行")

1. 如果您先前已設定任何發行的設定檔**發佈**窗格隨即出現。 選取 **建立新的設定檔**。

1. 在 **挑選發行目標**對話方塊方塊中，選擇**IIS、 FTP 等**。

    ![選擇 IIS、 FTP 等](../deployment/media/quickstart-publish-iis-ftp.png "選擇 IIS、 FTP 等。")

1. 選取 [發行]。 設定檔發佈的設定 對話方塊隨即開啟。

    ![選擇資料夾](../deployment/media/quickstart-publish-settings-web.png "選擇資料夾")

1. 在 **發行方法**欄位中，選擇一種方法，例如**Web Deploy**或是**FTP**。 您會看到的設定接下來會對應至您發佈的方法。 Web Deploy 可簡化部署到 IIS 伺服器，Web 應用程式和網站，並必須安裝為伺服器上的應用程式。 使用[Web platform installer](https://www.microsoft.com/web/downloads/platform.aspx)進行安裝。

1. 設定必要的設定的發佈方法，然後選取**驗證連線**。 如果有可用的伺服器或目標，而且您的設定是否正確，驗證訊息，指出連接時，且您已經準備好發行。

    ![驗證您的連線](../deployment/media/quickstart-publish-web-deploy.png "驗證您的連線")

1. 選取 **設定**若要設定其他的部署設定，例如是否要部署偵錯或發行組態，然後按**儲存**。 如果您要遠端偵錯，偵錯組態是必要的。

1. 若要發佈，請選取**發佈**。 [輸出] 視窗會顯示部署進度和結果。

## <a name="next-steps"></a>後續步驟

在本快速入門中，您已了解如何使用 Visual Studio 建立發行設定檔。 您也可以設定發佈設定檔匯入發佈設定。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 IIS](tutorial-import-publish-settings-iis.md)
