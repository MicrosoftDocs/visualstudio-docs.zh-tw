---
title: 部署到本機資料夾
description: 瞭解如何使用發佈工具將 ASP.NET、ASP.NET Core、.NET Core 和 Python 應用程式發佈至 Visual Studio 的資料夾。
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2b16c10d13f63be43ad2e8c3e16d24c0f9fd5e38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927427"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>使用 Visual Studio 將應用程式部署到資料夾

您可以使用 [ **發佈** ] 工具，將 ASP.NET、ASP.NET CORE、.net Core 和 Python 應用程式發佈至 Visual Studio 的資料夾。 針對 Node.js，支援這些步驟但使用者介面不同。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> 如果您需要將 Windows 桌面應用程式發佈到資料夾，請參閱 [使用 ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (c # 或 Visual Basic) 來部署傳統型應用程式。 針對 C++/CLR，請參閱[使用 ClickOnce 部署原生應用程式](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)，針對 C/C++，請參閱[使用安裝專案部署原生應用程式](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)。

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> 如果您需要將 .NET Core 3.1 或更新版本的 Windows 桌面應用程式發佈到資料夾，請參閱 [使用 ClickOnce 部署 .Net Windows 應用程式](quickstart-deploy-using-clickonce-folder.md)。

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>部署到本機資料夾

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![方案總管的專案內容功能表上的 [發行] 命令](../deployment/media/quickstart-publish.png "選擇 [發行]")

1. 如果您先前已設定任何發行設定檔，[ **發行** ] 視窗隨即出現。 選取 [ **新增**]。

1. 在 [ **發行** ] 視窗中，選取 [ **資料夾**]。

    ![選擇資料夾做為發佈目標](../deployment/media/quickstart-publish-folder-new.png "選擇資料夾")

::: moniker range=">=vs-2019"

4. 如果您要部署 .NET Core 3.1 或更新版本的 Windows 應用程式，您可能需要在 **特定目標** 視窗中選取 **資料夾**。

![選擇資料夾作為特定目標](../deployment/media/quickstart-publish-folder-targets.png "選擇特定目標")

5. 如果您想要使用 ClickOnce 發行 .NET Core 3.1 或更新版本的 Windows 應用程式，請參閱 [使用 Clickonce 部署 .Net Windows 應用程式](quickstart-deploy-using-clickonce-folder.md)。

 ::: moniker-end

4. 輸入路徑或選取 **[流覽]** 以指定資料夾。

    ![指定資料夾的路徑](../deployment/media/quickstart-publish-folder-path.png "選擇資料夾")

1. 選取 [發佈]。 Visual Studio 會建置專案，並將其發行至指定的資料夾。 專案屬性 [發行] 窗格隨即出現，並顯示設定檔摘要。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-publish-folder-summary.png)

1. 若要設定部署設定，請選取發行設定檔摘要中的 [ **編輯** ]，然後選取 [ **設定** ] 索引標籤。

   您看到的設定取決於您的應用程式類型。 下圖顯示 ASP.NET Core 應用程式的範例設定。

    ![設定檔設定](../deployment/media/quickstart-profile-settings.png "設定檔設定")

    如需在 .NET 中選擇設定的其他說明，請參閱下列各項：

    - [與 Framework 相依的 vs 獨立部署](/dotnet/core/deploying/)
    - [目標執行時間識別碼 (可攜的 RID，et al) ](/dotnet/core/rid-catalog)
    - [Debug 和 release 設定](../ide/understanding-build-configurations.md)

1. 設定選項，例如是否要部署 [偵錯] 或 [發行] 組態，然後選取 [儲存]。

1. 若要發行，請選取 [發行]。

請使用任何您想要的方式，部署已發行的檔案。 例如，您可以使用簡單的 copy 命令將它們封裝在 *.zip* 檔案中，或與您選擇的任何安裝套件一起部署。

## <a name="next-steps"></a>下一步

針對 .NET 應用程式：

- [使用發行工具部署 .NET Core 應用程式](/dotnet/core/deploying/deploy-with-vs)
- [.NET Core 應用程式發佈 (framework 相依與獨立部署) ](/dotnet/core/deploying/)
- [部署 .NET Framework 和應用程式](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [使用 ClickOnce 部署 .Net Windows 應用程式](quickstart-deploy-using-clickonce-folder.md)。
 ::: moniker-end
