---
description: 將應用程式封裝為 MSI 通常是使用 Visual Studio 安裝程式專案延伸模組來完成。
title: Visual Studio 安裝程式專案和 .NET Core 3。1
titleSuffix: ''
ms.date: 08/18/2020
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5a78c1cf4f7b1562408e0a3fb598075f2c114fc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171236"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Visual Studio 安裝程式專案延伸模組與 .NET Core 3.1

將應用程式封裝為 MSI 通常是使用 Visual Studio 安裝程式專案延伸模組來完成。

您可以在這裡下載延伸模組： [Visual Studio 安裝程式專案](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>適用于 .NET Core 的更新
.NET Core 有兩種不同的模型可供發佈。

- 與 Framework 相依的部署

- 獨立應用程式包括執行時間。

若要深入瞭解這些部署策略，請參閱 [.Net Core 應用程式發行總覽](/dotnet/core/deploying/)。

### <a name="workflow-changes-for-net-core-31"></a>.NET Core 3.1 的工作流程變更

1. 選取 [ **發行專案** ] 而非 [ **主要輸出** ]，以取得 .net Core 3.1 專案的正確輸出。  若要顯示此對話方塊，請  >  從專案的內容功能表中選取 [加入 **專案輸出 ...** ]。

    ![[加入專案輸出群組] 對話方塊中的 [發行專案] 輸出群組](../deployment/media/installer-projects-net-core-publish-items-output.png "挑選發行專案")

2. 若要建立獨立的安裝程式，請使用發行設定檔的相對路徑並設定正確的屬性，在安裝專案的 [**發行專案**] 節點上設定 **PublishProfilePath** 屬性。

    ![設定發行專案專案輸出專案的發行設定檔](../deployment/media/installer-projects-net-core-publish-profile.png "設定發行設定檔")

### <a name="prerequisites-for-net-core-31"></a>.NET Core 3.1 的必要條件

如果您想要讓安裝程式能夠安裝與 framework 相依之 .NET Core 3.1 應用程式所需的執行時間，您可以使用 [必要條件](../deployment/application-deployment-prerequisites.md)來執行此作業。  從安裝程式專案的 [屬性] 對話方塊中，開啟 [ **必要條件** ] 對話方塊，您會看到下列專案：

![必要條件對話方塊中的 .NET Core 專案](../deployment/media/installer-projects-net-core-prerequisites.png ".NET Core 的必要條件")

應選取 [ **.Net Core 執行時間 ...** ] 選項，以針對 WPF/WinForms 應用程式選取 [主控台應用程式]、[ **.net 桌面執行時間 ...** ]。

>[!NOTE]
>這些專案自 Visual Studio 2019 Update 7 發行開始存在。

## <a name="see-also"></a>另請參閱

- [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
