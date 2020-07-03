---
title: 建立和編輯組建組態
description: 本文描述如何在 Visual Studio for Mac 中建立組建組態
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: eb3ceed624e3bbba67564bb8f7c359841c0e496d
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939185"
---
# <a name="creating-and-editing-build-configurations"></a>建立和編輯組建組態

[組建設定] 可讓您精確地控制組建，讓您建立設定以滿足不同的測試和散佈狀況。 您可以建立個別專案的組建設定，或以整個方案為基礎。

您可以使用 [專案選項] 對話方塊，建立新的設定，並編輯專案和方案的現有設定。

>[!NOTE]
>本主題適用於 Visual Studio for Mac。 如需 Windows 上的 Visual Studio，請參閱[如何：建立和編輯](/visualstudio/ide/how-to-create-and-edit-configurations)設定。

## <a name="creating-a-project-build-configuration"></a>建立專案組建設定

若要建立專案組建設定，請遵循下列步驟：

1. 以滑鼠右鍵按一下專案節點，然後選取 [選項]****。 您也可以按兩下專案節點，以顯示 [專案選項] 對話方塊。

2. 在專案選項對話方塊中，選取 [組建] > [組態]****：

    ![專案選項中的組態管理員](media/create-and-edit-configurations-image2.png)

3. 選取 **[新增]** 以建立新的設定。 您也可以複製任何現有的設定。

建立設定之後，您可以使用 [專案] 選項中的 [**組建**] 區段，來調整適用于您設定的屬性：

![設定組建選項](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>建立方案組建組態

若要建立解決方案組建設定，請遵循下列步驟：

1. 以滑鼠右鍵按一下方案節點，然後選取 [**選項**]。 您也可以按兩下 [方案] 節點，以顯示 [方案選項] 對話方塊。

2. 在 [方案選項] 對話方塊中，選取 [組建] > [組態]****：

    ![方案選項中的組態管理員](media/create-and-edit-configurations-image1.png)

3. 選取 **[新增]** 以建立新的設定。 您也可以複製任何現有的設定。

建立設定之後，您可以使用每個專案之 [專案選項] 對話方塊的 [**組建**] 區段，來調整您的設定適用的屬性：

![設定組建選項](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>重新命名組建設定

若要重新命名設定，請從 [設定] 清單中選取它，方法是流覽至 [專案] 或 [方案] 選項中的 [**建立 >** 設定]

![組態清單](media/create-and-edit-configurations-image4.png)

選取 [重新命名]**** 按鈕。

![重新命名對話方塊](media/create-and-edit-configurations-image5.png)

然後按一下 **[確定]** 以確認。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>另請參閱

- [建立和編輯組建組態 (Windows 上的 Visual Studio)](/visualstudio/ide/how-to-create-and-edit-configurations)