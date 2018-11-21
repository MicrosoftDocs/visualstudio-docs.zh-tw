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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781909"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>使用 Visual Studio 將應用程式部署到本機資料夾

您可以使用 [發行] 工具，從 Visual Studio 將 ASP.NET、ASP.NET Core、.NET Core 及 Python 應用程式發行至本機資料夾。 針對 Node.js，支援這些步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>部署到本機資料夾

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![[方案總管] 中專案操作功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您之前已設定任何發行設定檔，[發行] 窗格隨即出現。 選取 [建立新設定檔]。

1. 在 [挑選發行目標] 對話方塊中，選擇 [資料夾]。

    ![選擇本機資料夾作為發行目標](../deployment/media/quickstart-publish-folder.png "選擇 [資料夾]")

1. 輸入路徑，或選取 [瀏覽] 來指定本機資料夾。

1. 選取 [發行]。 Visual Studio 會建置專案，並將其發行至指定的資料夾。 專案屬性 [發行] 窗格隨即出現，並顯示設定檔摘要。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-folder-summary.png)

1. 若要設定部署設定，請在設定檔摘要中選取 [設定]，並選取 [設定] 索引標籤。

    ![設定檔設定](../deployment/media/quickstart-profile-settings.png "設定檔設定")

1. 設定選項，例如是否要部署 [偵錯] 或 [發行] 組態，然後選取 [儲存]。

1. 若要發行，請選取 [發行]。

請使用任何您想要的方式，部署已發行的檔案。 例如，您可以使用簡單的 copy 命令將它們封裝在 *.zip* 檔案中，或與您選擇的任何安裝套件一起部署。

## <a name="next-steps"></a>後續步驟

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [為 Microsoft Store (傳統型橋接器) 封裝傳統型應用程式](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [部署 .NET Framework 和應用程式](/dotnet/framework/deployment/)
