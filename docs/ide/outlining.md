---
title: 摺疊和展開程式碼的區域
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781c9a6bc30f7d3a29bcb89e743600e6b29e6445
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585752"
---
# <a name="outlining"></a>大綱

您可以選擇通過折疊代碼區域來隱藏某些代碼，以便代碼顯示在加號 （ ）**+** 下。 您可以按一下加號來展開已摺疊的區域 如果您是鍵盤使用者，則可以選擇**Ctrl**+**M M**+**M**折疊和展開。 您也可以摺疊大綱區域，方法是按兩下大綱邊界之區域中的任一行，而大綱邊界出現在程式碼左邊。 當您將滑鼠停留在已摺疊的區域上方時，已摺疊區域的內容會成為工具提示。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[原始檔編輯器 (Visual Studio for Mac )](/visualstudio/mac/source-editor)。

當您將滑鼠停留在邊界上方時，也會反白顯示大綱邊界中的區域。 在某些色彩組態中，預設反白顯示色彩似乎太過模糊。 您可以在**工具** > **選項** > **Environment**環境 > **字體和顏色** > **可折疊區域**中更改它。

當您使用大綱程式碼時，可以展開您想要處理的區段，並在完成時予以摺疊，然後移至其他區段。 當您不想要顯示大綱時，可以使用 [取消大綱]**** 命令以移除大綱資訊，而不干擾基礎程式碼。

[編輯]**** 功能表上的 [復原]**** 和 [重做]**** 命令會影響這些動作。 [複製]****、[剪下]****、[貼上]**** 和拖放作業都會保留大綱資訊，而不是可摺疊區域的狀態。 例如，當您複製已摺疊的區域時，[貼上]**** 作業會將複製的文字貼為已展開的區域。

> [!CAUTION]
> 當您變更大綱區域時，可能會遺失大綱。 例如，刪除或 [尋找] 和 [取代] 作業可能會清除區域的結尾。

可在 **"編輯** > **大綱**"子功能表上找到以下命令。

|||
|-|-|
|隱藏選取範圍|（**Ctrl**+**M，** **Ctrl**+**H**） - 折疊選定的代碼塊，該代碼塊通常不能大綱排列，`if`例如塊。 若要移除自訂區域，請使用 [取消隱藏目前大綱]**** (或 **Ctrl**+**M**、**Ctrl**+**U**)。 在 Visual Basic 中無法使用。|
|切換大綱展開|- 在游標落在巢狀摺疊區段時，反轉最內層大綱區段的目前隱藏或展開狀態。|
|切換所有大綱|**（Ctrl**+**M，** **Ctrl**+**L**） - 將所有地區設定為相同的折疊或展開狀態。 如果有些區域展開，有些區域摺疊，則會展開摺疊區域。|
|取消大綱|**（Ctrl**+**M**， **Ctrl**+**P**） - 刪除整個文檔的所有大綱資訊。|
|取消隱藏目前的|**（Ctrl**+**M**， **Ctrl**+**U**） - 刪除當前選定的使用者定義的區域的大綱資訊。 在 Visual Basic 中無法使用。|
|摺疊至定義|（**Ctrl**+**M**， **Ctrl**+**O**） - 折疊所有類型的成員。|
|摺疊區塊︰\<邏輯界限>|（C++）折疊包含插入點的函數中的區域。 例如，如果插入點落在迴圈內，則會隱藏迴圈。|
|\<邏輯結構> 中的全部摺疊|（C++）折疊函數內的所有結構。|

您也可以使用 Visual Studio SDK 來定義您想要展開或摺疊的文字區域。 請參閱[逐步解說︰大綱](../extensibility/walkthrough-outlining.md)。

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能](../ide/writing-code-in-the-code-and-text-editor.md)
- [原始檔編輯器 (Visual Studio for Mac)](/visualstudio/mac/source-editor)
