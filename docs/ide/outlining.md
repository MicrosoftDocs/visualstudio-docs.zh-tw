---
title: 摺疊和展開程式碼的區域
description: 瞭解如何在 Visual Studio 中使用展開和折迭命令以大綱模式運作
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04a2156723bc33e25a658814b9348655f7ba86d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909063"
---
# <a name="outlining"></a>大綱

您可以選擇隱藏一些程式碼，方法是折迭程式碼區域，使其出現在加號 (**+**) 。 您可以按一下加號來展開已摺疊的區域 如果您是鍵盤使用者，您可以選擇 **Ctrl** + **M** + **m** 以折迭和展開。 您也可以摺疊大綱區域，方法是按兩下大綱邊界之區域中的任一行，而大綱邊界出現在程式碼左邊。 當您將滑鼠停留在已摺疊的區域上方時，已摺疊區域的內容會成為工具提示。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[原始檔編輯器 (Visual Studio for Mac )](/visualstudio/mac/source-editor)。

當您將滑鼠停留在邊界上方時，也會反白顯示大綱邊界中的區域。 在某些色彩組態中，預設反白顯示色彩似乎太過模糊。 您可以在 [**工具**  >  **選項**]  >  **環境** 字型  >  **和**  >  ****[可折迭區域] 中變更它。

當您使用大綱程式碼時，可以展開您想要處理的區段，並在完成時予以摺疊，然後移至其他區段。 當您不想要顯示大綱時，可以使用 [取消大綱] 命令以移除大綱資訊，而不干擾基礎程式碼。

[編輯] 功能表上的 [復原] 和 [重做] 命令會影響這些動作。 [複製]、[剪下]、[貼上] 和拖放作業都會保留大綱資訊，而不是可摺疊區域的狀態。 例如，當您複製已摺疊的區域時，[貼上] 作業會將複製的文字貼為已展開的區域。

> [!CAUTION]
> 當您變更大綱區域時，可能會遺失大綱。 例如，刪除或 **尋找和取代** 作業可能會清除區域結尾。

您可以在 [**編輯**  >  **大綱**] 子功能表中找到下列命令。

|名稱|描述|
|-|-|
|隱藏選取範圍| (**ctrl** + **M**、 **ctrl** + **H**) -折迭選取的程式碼區塊，通常不能用於大綱，例如 `if` 區塊。 若要移除自訂區域，請使用 [取消隱藏目前大綱] (或 **Ctrl**+**M**、**Ctrl**+**U**)。 在 Visual Basic 中無法使用。|
|切換大綱展開|  (**ctrl** + **m**、 **ctrl** + **m**) -當游標位於嵌套折迭的區段時，將最內層大綱區段的目前隱藏或展開狀態反轉。|
|切換所有大綱| (**ctrl** + **M**、 **ctrl** + **L**) -將所有區域設定為相同的折迭或展開狀態。 如果有些區域展開，有些區域摺疊，則會展開摺疊區域。|
|取消大綱| (**ctrl** + **M**、 **ctrl** + **P**) -移除整份檔的所有大綱資訊。|
|取消隱藏目前的| (**ctrl** + **M**、 **ctrl** + **U**) -移除目前所選取使用者定義區域的大綱資訊。 在 Visual Basic 中無法使用。|
|摺疊至定義| (**ctrl** + **M**、 **ctrl** + **O**) -折迭所有類型的成員。|
|折迭區塊：\<logical boundary>| (c + +) 折迭包含插入點的函式區域。 例如，如果插入點落在迴圈內，則會隱藏迴圈。|
|全部折迭： \<logical structures>| (c + +) 折迭函數內部的所有結構。|

您也可以使用 Visual Studio SDK 來定義您想要展開或摺疊的文字區域。 請參閱[逐步解說︰大綱](../extensibility/walkthrough-outlining.md)。

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [原始檔編輯器 (Visual Studio for Mac)](/visualstudio/mac/source-editor)
