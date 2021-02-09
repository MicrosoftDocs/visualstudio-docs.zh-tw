---
title: 如何：建立和編輯組態
description: 瞭解如何使用 Visual Studio 來建立和編輯解決方案的數個組建設定。
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 636fbabbede90d9a1c686a2252aef712b4789c18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878717"
---
# <a name="how-to-create-and-edit-configurations"></a>如何：建立和編輯組態

您可以為方案建立數個組建組態。 例如，您可以設定偵錯組建讓測試人員可以用來尋找和修正問題，也可以設定不同類型的組建，散發給不同的客戶。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [在 Visual Studio for Mac 中建立和編輯組態](/visualstudio/mac/create-and-edit-configurations)。

## <a name="create-build-configurations"></a>建立組建組態

您可以使用 [組態管理員] 對話方塊來選取或修改現有的組建組態，或是建立新的組建組態。

若要開發 [組態管理員] 對話方塊，請在 **方案總管** 中，開啟方案的捷徑功能表，然後選擇 [組態管理員]。

> [!NOTE]
> 如果 **Configuration Manager** 命令未出現在捷徑功能表，請查看功能表列上的 [建置] 功能表底下。 如果未出現在功能表列上，請選擇 [**工具**  >  **選項**]，然後在 [**選項**] 對話方塊的左窗格中，展開 [**專案和方案**]，然後  >  在右窗格中選取 [**顯示 advanced build** configuration] 核取方塊。

在 [Configuration Manager] 對話方塊中，您可以使用 [使用中的方案組態] 下拉式清單選取整個方案的組建組態、修改現有的組建組態，或建立新的組態。 您可以使用 [使用中的方案平台] 下拉式清單選取組態目標針對的平台、修改現有的方案平台，或新增平台。 [專案內容] 窗格會列出方案中的專案。 針對每個專案，您可以選取專案特定的組態與平台、修改現有的組態與平台，或建立新的組態或新增平台。 您也可以選取核取方塊，指出當您使用整個方案的組態來建置或部署方案時，是否包含每個專案。

設定您需要的組態之後，您可以設定適用於這些組態的專案屬性。

### <a name="set-properties-based-on-configurations"></a>根據組態來設定屬性

若要根據組態來設定屬性，請在 [方案總管] 中，開啟專案的捷徑功能表，然後選擇 [屬性]。 您可以設定組態的屬性。 例如，針對版本組態，您可以指定在建置方案時將程式碼最佳化，而針對偵錯組態，您可以指定包含 `DEBUG` 條件式編譯符號。

如需屬性頁設定的詳細資訊，請參閱[管理專案和方案屬性](../ide/managing-project-and-solution-properties.md)。

## <a name="create-a-project-configuration"></a>建立專案組態

1. 開啟 [組態管理員] 對話方塊。

2. 選取 [專案] 資料行中的專案。

3. 在該專案的 [組態] 下拉式清單中，選擇 [新增]。

     [新增專案組態] 對話方塊隨即開啟。

4. 在 [名稱] 方塊中，輸入新組態的名稱。

5. 若要使用來自現有專案組態的屬性設定，請在 [複製設定值來源] 下拉式清單中，選擇組態。

6. 若要同時建立整個方案的組態，請選取 [建立新方案組態] 核取方塊。

## <a name="rename-a-project-configuration"></a>重新命名專案組態

1. 開啟 [組態管理員] 對話方塊。

2. 在 [專案] 資料行中，選取具有您想要重新命名之專案組態的專案。

3. 在該專案的 [組態] 下拉式清單中，選擇 [編輯]。

     [編輯專案組態] 對話方塊隨即開啟。

4. 選取您想要變更的專案組態名稱。

5. 選取 [重新命名]，然後輸入新名稱。

## <a name="create-and-modify-solution-wide-build-configurations"></a>建立和修改整個方案的組建組態

### <a name="to-create-a-solution-wide-build-configuration"></a>建立整個方案的組建組態

1. 開啟 [組態管理員] 對話方塊。

2. 在 [使用中的方案組態] 下拉式清單中，選擇 [新增]。

     [新增方案組態] 對話方塊隨即開啟。

3. 在 [名稱] 文字方塊中，輸入新組態的名稱。

4. 若要使用來自現有方案組態的設定，請在 [複製設定值來源] 下拉式清單中，選擇組態。

5. 如果您想要同時建立專案組態，請選取 [建立新的專案組態] 核取方塊。

### <a name="to-rename-a-solution-wide-build-configuration"></a>重新命名整個方案的組建組態

1. 開啟 [組態管理員] 對話方塊。

2. 在 [使用中的方案組態] 下拉式清單中，選擇 [編輯]。

     [編輯方案組態] 對話方塊隨即開啟。

3. 選取您想要變更的方案組態名稱。

4. 選取 [重新命名]，然後輸入新名稱。

### <a name="to-modify-a-solution-wide-build-configuration"></a>修改整個方案的組建組態

1. 開啟 [組態管理員] 對話方塊。

2. 在 [使用中的方案組態] 下拉式清單中，選取您想要的組態。

3. 在 [專案內容] 窗格中，針對每個專案選取您要的 [組態] 和 [平台]，然後選取是否要 [建置] 它，以及是否要 [部署] 它。

## <a name="see-also"></a>另請參閱

- [了解組建組態](../ide/understanding-build-configurations.md)
- [在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [管理專案和解決方案屬性](managing-project-and-solution-properties.md)
- [建立和編輯組態 (Visual Studio for Mac)](/visualstudio/mac/create-and-edit-configurations)
