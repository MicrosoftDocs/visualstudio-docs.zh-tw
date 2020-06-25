---
title: 部署到本機資料夾
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da13cb2b249146c7a29abbab03b66f77594abf4b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285398"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>使用 Visual Studio 將應用程式部署到本機資料夾

您可以使用 [發行]**** 工具，從 Visual Studio 將 ASP.NET、ASP.NET Core、.NET Core 及 Python 應用程式發行至本機資料夾。 針對 Node.js，支援這些步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> 如果您需要將 Windows 桌面應用程式發行至本機資料夾，請參閱[使用 ClickOnce 部署桌面應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# 或 Visual Basic)。 針對 C++/CLR，請參閱[使用 ClickOnce 部署原生應用程式](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)，針對 C/C++，請參閱[使用安裝專案部署原生應用程式](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)。

## <a name="deploy-to-a-local-folder"></a>部署到本機資料夾

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行]**** (或使用 [建置]**** > [發行]**** 功能表項目)。

    ![[專案] 內容功能表上的 [發佈] 命令方案總管](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 在 [**發行**] 對話方塊中，選取 [**資料夾**]。

    ![選擇資料夾作為發佈目標](../deployment/media/quickstart-publish-folder-new.png "選擇資料夾")

1. 輸入路徑，或選取 **[流覽]** 以指定資料夾。

    ![指定資料夾的路徑](../deployment/media/quickstart-publish-folder-path.png "選擇資料夾")

1. 選取 [發佈] 。 Visual Studio 會建置專案，並將其發行至指定的資料夾。 專案屬性 [發行]**** 窗格隨即出現，並顯示設定檔摘要。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-folder-summary.png)

1. 若要設定部署設定，請選取發行設定檔摘要中的 [**編輯**]，然後選取 [**設定**] 索引標籤。

    ![設定檔設定](../deployment/media/quickstart-profile-settings.png "設定檔設定")

1. 設定選項，例如是否要部署 [偵錯] 或 [發行] 組態，然後選取 [儲存]****。

1. 若要發行，請選取 [發行]****。

請使用任何您想要的方式，部署已發行的檔案。 例如，您可以使用簡單的 copy 命令將它們封裝在 *.zip* 檔案中，或與您選擇的任何安裝套件一起部署。

## <a name="next-steps"></a>後續步驟

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [為 Microsoft Store (傳統型橋接器) 封裝傳統型應用程式](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [部署 .NET Framework 和應用程式](/dotnet/framework/deployment/)
