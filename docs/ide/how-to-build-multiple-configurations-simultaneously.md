---
title: 如何：建立多個設定
description: 瞭解如何使用一個 IDE 動作來建立大部分類型的專案，其中包含多個或甚至所有的組建設定。
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cabaf226742d867e9d5eccbaf391b723cfbed5d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967666"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>如何：在單一組建要求中建立多個設定

您可以使用 [ **批次組建** ] 對話方塊，以一個 IDE 動作來建立大部分類型的專案，其中包含多個或甚至全部的組建設定。 不過，您無法同時在多個組建組態中組建下列類型的專案：

1. [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式是使用 JavaScript 針對 Windows 建置。

2. 所有 Visual Basic 專案。

3. CMake 專案。

如果解決方案包含這兩種專案類型的任何專案，則該解決方案無法使用 **批次組建** 。 在此情況下，此命令不會出現在 [ **組建** ] 功能表上。

   如需組建組態的詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)。

## <a name="to-build-a-project-in-multiple-build-configurations"></a>在多個組建組態中建置專案

1. 在功能表列上，選擇 [**建立**  >  **批次組建**]。 或者，按 **Ctrl** + **Q** 開啟 [搜尋] 方塊，然後搜尋 `Batch Build` 。

2. 在 [建置] 資料行中，選取您要用來建置專案之組態的核取方塊。

    > [!TIP]
    > 若要編輯或建立方案的組建設定，請選擇功能表列上的 [**建立**  >  **設定管理員**]，以開啟 [**設定管理員**] 對話方塊。 在您編輯方案的組建組態之後，請在 [批次建置] 對話方塊中選擇 [重建] 按鈕，來更新方案中專案的所有組建組態。

3. 選擇 [建置] 或 [重建] 按鈕，以使用您指定的組態來建置專案。

## <a name="see-also"></a>另請參閱

- [如何：建立和編輯設定](../ide/how-to-create-and-edit-configurations.md)
- [了解組建組態](../ide/understanding-build-configurations.md)
- [平行建立多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)