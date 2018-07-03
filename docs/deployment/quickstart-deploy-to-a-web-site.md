---
title: 發行至網站-Visual Studio |Microsoft 文件
ms.custom: ''
ms.date: 11/22/2017
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
ms.openlocfilehash: 0f722dcc4ada5643f9de3342b85469fa667d4b7c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766548"
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>將 web 應用程式或.NET Core 應用程式發行至網站，使用 Visual Studio 發行工具

您可以使用**發行**發佈到網站的 ASP.NET 應用程式的工具。

這些步驟適用於 ASP.NET、 ASP.NET Core、.NET Core 和 Visual Studio 的 Python 應用程式。 For Node.js，所支援的步驟，但是使用者介面不同。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 和**ASP.NET 及 web 開發**工作負載和。**NET 桌面開發**工作負載。 .NET Core 應用程式中，您需要。*.NET Core**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

1. 在下**Visual C#** 或**Visual Basic**，選擇**Web**，然後在中間窗格中選擇  **ASP.NET Web 應用程式 (.NET Framework)**（僅限 C#) 或**ASP.NET Core Web 應用程式**，然後按一下 **確定**。

1. 選擇**MVC** (或選擇**Web 應用程式 （模型-檢視-控制器）** 適用於.NET Core)，請確定**非驗證**已選取，然後按一下 **[確定]**.

1. 輸入的名稱，例如**MyWebApp**按一下**確定**。

    Visual Studio 會建立專案。

1. 選擇**建置 > 建置方案**建置專案。

## <a name="publish-to-a-web-site"></a>發行至網站

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。

    ![選擇發行](../deployment/media/quickstart-publish-aspnet.png "選擇發行")

1. 如果您先前設定的任何發行設定檔，**發行** 窗格隨即出現。 按一下**建立新的設定檔**。

1. 在**挑選發行目標**對話方塊方塊中，選擇**IIS，FTP 等**。

    ![選擇 IIS、 FTP、 等](../deployment/media/quickstart-publish-iis-ftp.png "選擇 IIS、 FTP 和其他內容。")

1. 按一下 [發行] 。

    設定檔發佈的設定 對話方塊隨即開啟。

    ![選擇資料夾](../deployment/media/quickstart-publish-settings-web.png "選擇資料夾")

1. 在**發行方法**欄位中，選擇一種方法，例如**Web Deploy**或**FTP**。

    您會看到的設定下一步對應加入至發行的方法。 Web Deploy，可簡化部署的 Web 應用程式和網站的 IIS 伺服器，並必須安裝為伺服器上的應用程式。 使用[Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)來安裝它。

1. 設定發行方法所需要的設定，按一下**驗證連線**。

    如果伺服器或目標可供使用，而且您設定正確，您會看到一個訊息，指出連線已經驗證，而且準備要發行。

    ![驗證您的連線](../deployment/media/quickstart-publish-web-deploy.png "驗證您的連線")

1. 如果您想要設定其他部署設定，請按一下**設定**。

    您可以設定選項，例如是否要部署的偵錯或發行組態，然後按**儲存**。 如果您遠端偵錯，偵錯組態需要。

1. 若要發行，按一下 **發行**。

    [輸出] 視窗會顯示部署進度和結果。

## <a name="next-steps"></a>後續步驟

本快速入門中，您學會如何使用 Visual Studio 建立的發行設定檔。 您也可以設定的發行設定檔匯入發行設定。

> [!div class="nextstepaction"]
> [匯入發佈設定並部署至 IIS](tutorial-import-publish-settings-iis.md)
