---
title: 將部署到本機資料夾-Visual Studio |Microsoft 文件
ms.custom: ''
ms.date: 05/08/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016538bded47a5186294c161cc7f310b26818d15
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764215"
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>將 web 應用程式或.NET Core 應用程式部署至本機資料夾，使用 Visual Studio 發行工具

您可以使用**發行**工具，以將您的應用程式發行至本機資料夾。 

這些步驟適用於 ASP.NET、 ASP.NET Core、.NET Core 和 Visual Studio 的 Python 應用程式。 For Node.js，所支援的步驟，但是使用者介面不同。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 和。**.NET 桌面開發**工作負載而。**.NET Core**工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-new-project"></a>建立新專案 

1. 在 Visual Studio 中，選擇 [檔案] > [新增專案]。

1. 在下**Visual C#** 或**Visual Basic**，選擇 **.NET Core**，然後在中間窗格中選擇 **主控台應用程式 (.NET Core)**。

1. 輸入的名稱，例如**MyLocalApp**按一下**確定**。

    Visual Studio 會建立專案。

## <a name="deploy-to-a-local-folder"></a>部署到本機資料夾

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。

    ![選擇發行](../deployment/media/quickstart-publish.png "選擇發行")

1. 如果您先前設定的任何發行設定檔，**發行** 窗格隨即出現。 按一下**建立新的設定檔**。

1. 在**挑選發行目標**對話方塊方塊中，選擇**資料夾**。

    ![選擇資料夾](../deployment/media/quickstart-publish-folder.png "選擇資料夾")

1. 輸入路徑，或按一下**瀏覽**瀏覽至本機資料夾。

1. 按一下 [發行] 。

    Visual Studio 建置專案，並將其發佈至指定的資料夾。

    [發行] 窗格會顯示摘要的設定檔。

1. 若要設定部署設定，請按一下**設定**摘要的設定檔中。

    ![設定檔設定](../deployment/media/quickstart-profile-settings.png "設定檔設定") 

1. 設定選項，例如是否要部署的偵錯或發行組態，然後按**儲存**。

1. 若要重新發佈，請按一下**發行**。

請使用任何您想要的方式，部署已發行的檔案。 比方說，您可以加以封裝 Zip 檔案中，使用簡單的複製命令，或將其部署與您所選擇的任何安裝套件。

## <a name="next-steps"></a>後續步驟

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [為 Microsoft Store (傳統型橋接器) 封裝傳統型應用程式](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET)[部署.NET Framework 和應用程式...](/dotnet/framework/deployment/)
