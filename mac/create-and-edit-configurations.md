---
title: 建立和編輯組建組態
description: 本文描述如何在 Visual Studio for Mac 中建立組建組態
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128429"
---
# <a name="creating-and-editing-build-configurations"></a>建立和編輯組建組態

組建組態使您能夠精確控制生成，從而允許您創建配置以滿足不同的測試和分發情況。 您可以為單個專案或解決方案範圍創建組建組態。

您可以使用"專案選項"對話方塊為專案和解決方案創建新配置並編輯現有配置。

>[!NOTE]
>本主題適用於 Visual Studio for Mac。 有關 Windows 上的視覺化工作室，請參閱[操作操作：創建和編輯配置](/visualstudio/ide/how-to-create-and-edit-configurations)。

## <a name="creating-a-project-build-configuration"></a>創建專案組建組態

要創建專案組建組態，請按照以下步驟操作：

1. 以滑鼠右鍵按一下專案節點，然後選取 [選項]****。 您還可以按兩下專案節點以彈出"專案選項"對話方塊。

2. 在專案選項對話方塊中，選取 [組建] > [組態]****：

    ![專案選項中的組態管理員](media/create-and-edit-configurations-image2.png)

3. 選擇 **"添加"** 以創建新配置。 您還可以複製任何現有配置。

創建配置後，可以使用"專案選項"中的 **"生成**"部分來調整適合您的配置的屬性：

![設定組建選項](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>建立方案組建組態

要創建解決方案組建組態，請按照以下步驟操作：

1. 按右鍵解決方案節點並選擇 **"選項**"。 您還可以按兩下解決方案節點以彈出"解決方案選項"對話方塊。

2. 在 [方案選項] 對話方塊中，選取 [組建] > [組態]****：

    ![方案選項中的組態管理員](media/create-and-edit-configurations-image1.png)

3. 選擇 **"添加"** 以創建新配置。 您還可以複製任何現有配置。

創建配置後，可以使用每個專案的"專案選項"對話方塊的 **"生成**"部分來調整適合配置的屬性：

![設定組建選項](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>重命名組建組態

要重命名配置，請通過導航到"專案"或"解決方案選項"中的**生成>配置**，從"配置"清單中選擇它：

![組態清單](media/create-and-edit-configurations-image4.png)

選取 [重新命名]**** 按鈕。

![重新命名對話方塊](media/create-and-edit-configurations-image5.png)

然後按一下 **"確定"** 以確認。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>另請參閱

- [建立和編輯組建組態 (Windows 上的 Visual Studio)](/visualstudio/ide/how-to-create-and-edit-configurations)