---
title: 使用 ClickOnce 部署 .NET Windows 桌面應用程式
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5a6f7c2c8d6c79270df94c100bbd4625856efa15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934503"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>使用 ClickOnce 部署 .NET Windows 桌面應用程式

從 Visual Studio 2019 版本16.8 開始，您可以使用 **發行** 工具，從 Visual Studio 使用 ClickOnce 發行 .net Core 3.1 或更新版本的 Windows 桌面應用程式。

> [!NOTE]
> 如果您需要發佈 .NET Framework Windows 應用程式，請參閱 [使用 ClickOnce 部署桌面應用程式](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (c # 或 Visual Basic) 。

## <a name="publishing-with-clickonce"></a>使用 ClickOnce 發行

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選擇 [發行] (或使用 [建置] > [發行] 功能表項目)。

    ![方案總管的專案內容功能表上的 [發行] 命令](../deployment/media/quickstart-clickonce-solution-explorer.png "選擇 [發行]")

1. 如果您先前已設定任何發行設定檔，[ **發行** ] 頁面隨即出現。 選取 [ **新增**]。

1. 在 [ **發佈** 嚮導] 中，選取 [ **資料夾**]。

    ![選擇資料夾做為發佈目標](../deployment/media/quickstart-clickonce-publish-folder-category.png "選擇資料夾")

1. 在特定的 [ **目標** ] 頁面中，選取 [ **ClickOnce**]。

    ![選取 ClickOnce 作為特定目標](../deployment/media/quickstart-clickonce-publish-folder-target.png "選擇 ClickOnce")

1. 輸入路徑，或選取 **[流覽]** 以選取發行位置。

    ![指定發佈位置的路徑](../deployment/media/quickstart-clickonce-publish-location.png "輸入路徑")

1. 在 [ **安裝位置** ] 頁面中，選取使用者將安裝應用程式的位置。

    ![指定資料夾的路徑](../deployment/media/quickstart-clickonce-install-location.png "選擇安裝位置")

1. 在 [ **設定** ] 頁面中，您可以提供 ClickOnce 所需的設定。

1. 如果您選取從 UNC 路徑或網站安裝，此頁面可讓您指定應用程式是否可以離線使用。 選取此選項時，此選項會在使用者的 [開始] 功能表上列出應用程式，並允許應用程式在發行新版本時自動更新。 根據預設，您可以從安裝位置取得更新。  如果您想要讓更新有不同的位置，您可以使用 [更新設定] 連結來指定。 如果您不想讓應用程式離線使用，它會從安裝位置執行。

    ![指定發行設定](../deployment/media/quickstart-clickonce-unc-settings.png "選擇發行設定")

1. 如果您選擇從 CD、DVD 或 USB 磁片磁碟機安裝，此頁面也可讓您指定應用程式是否支援自動更新。 如果您選取支援更新，則更新位置是必要的，而且必須是有效的 UNC 路徑或網站。

    ![選擇發行設定](../deployment/media/quickstart-clickonce-settings.png "選擇發行設定")

此頁面中包含的功能，可以指定要包含在安裝程式中的 **應用程式檔** 、要安裝的 **必要條件** 套件，以及透過頁面頂端連結的其他 **選項** 。

此外，您也可以在此頁面中設定發行版本，並在每次發行時自動遞增版本。

> [!NOTE]
> 每個 ClickOnce 設定檔的發行版本號碼都是唯一的。 如果您計畫有多個設定檔，就必須記住這一點。

10. 在 [ **簽署資訊清單** ] 頁面中，您可以指定是否應簽署資訊清單，以及要使用的憑證。

    ![簽署 ClickOnce 資訊清單](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. **在 [設定] 頁面上**，您可以選取所需的專案設定。

     ![指定發佈設定](../deployment/media/quickstart-clickonce-configuration.png)

    如需有關要選擇哪一項設定的其他說明，請參閱下列各項：

    - [與 Framework 相依的 vs 獨立部署](/dotnet/core/deploying/)
    - [目標執行時間識別碼 (可攜的 RID，et al) ](/dotnet/core/rid-catalog)
    - [Debug 和 release 設定](../ide/understanding-build-configurations.md)

1. 選取 **[完成]** 以儲存新的 ClickOnce 發行設定檔。

1. 在 [ **摘要** ] 頁面上，選取 [ **發行** ]，Visual Studio 建立專案，並將其發行至指定的發行資料夾。 此頁面也會顯示設定檔摘要。

    ![顯示設定檔摘要的 [發行] 屬性窗格](../deployment/media/quickstart-clickonce-summary.png)

1. 若要發行，請選取 [發行]。

## <a name="next-steps"></a>下一步

針對 .NET 應用程式：

- [部署 .NET Framework 和應用程式](/dotnet/framework/deployment/)
- [ClickOnce 參考](clickonce-reference.md)
