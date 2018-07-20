---
title: 部署到本機資料夾
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781909"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>將應用程式部署到使用 Visual Studio 的本機資料夾

您可以使用**發佈**工具，從 Visual Studio 將 ASP.NET、 ASP.NET Core、.NET Core 及 Python 應用程式發行至本機資料夾。 適用於 Node.js，支援步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>部署到本機資料夾

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇**發佈**(或使用**建置** > **發佈**功能表項目)。

    ![在 [方案總管] 中的 [專案] 內容功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇發行")

1. 如果您先前已設定任何發行的設定檔**發佈**窗格隨即出現。 選取 **建立新的設定檔**。

1. 在 **挑選發行目標**對話方塊方塊中，選擇**資料夾**。

    ![選擇發行目標的本機資料夾](../deployment/media/quickstart-publish-folder.png "選擇資料夾")

1. 輸入路徑，或選取**瀏覽**來指定本機資料夾。

1. 選取 [發行]。 Visual Studio 會建置專案，並將其發佈到指定的資料夾。 專案屬性**發佈**窗格出現時，顯示設定檔摘要。

    ![發佈屬性窗格中顯示的設定檔摘要](../deployment/media/quickstart-publish-folder-summary.png)

1. 若要設定部署設定，請選取**設定**摘要並選取設定檔中**設定** 索引標籤。

    ![設定檔設定](../deployment/media/quickstart-profile-settings.png "設定檔設定")

1. 設定選項，例如是否要部署偵錯或發行組態，然後按**儲存**。

1. 若要重新發佈，請選取**發佈**。

請使用任何您想要的方式，部署已發行的檔案。 比方說，您可以封裝在 *.zip*檔案、 使用簡單的複製命令，或與您選擇的任何安裝封裝一起部署。

## <a name="next-steps"></a>後續步驟

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [為 Microsoft Store (傳統型橋接器) 封裝傳統型應用程式](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET)[部署.NET Framework 和應用程式](/dotnet/framework/deployment/)
