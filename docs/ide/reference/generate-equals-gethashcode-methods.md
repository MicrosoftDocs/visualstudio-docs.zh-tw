---
title: 產生 C# Equals 與 GetHashCode 方法的覆寫
description: 瞭解如何使用 [快速動作與重構] 功能表來產生 Equals 和 GetHashCode 方法。
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 04c054dd73e437907c0943e3e6f0af5003dee37e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962778"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>在 Visual Studio 中產生 Equals 與 GetHashCode 方法覆寫

此程式碼產生適用於：

- C#

**功能：** 讓您產生 **Equals** 與 **GetHashCode** 方法。

**時機：** 當您有某個類型應由一或多個欄位比對，而不是由記憶體中的物件位置比對時，請產生這些覆寫。

**為什麼：**

- 如果您要實作實值型別，便應該考慮覆寫 **Equals** 方法，以獲得比在 ValueType 上實作預設 Equals 方法更好的效能。

- 如果您要實作參考型別，當該類型看似基底類型 (例如 Point、String、BigNumber 等) 時，便應該考慮覆寫 **Equals** 方法。

- 覆寫 **GetHashCode** 方法以允許類型在雜湊表中正確運作。 如需更多指引，請參閱[等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)。

## <a name="how-to"></a>使用方法

1. 將游標放在型別宣告行的某個位置。

   ![醒目標示的程式碼](media/overrides-highlight-cs.png)

   > [!TIP]
   > 請勿按兩下來選取型別名稱，否則功能表選項將無法使用。 只要將游標放在該行的某個位置即可。

1. 接著，執行下列其中一項操作：

   - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。

   - 按一下 ![螺絲起子](../media/screwdriver-icon.png) 圖示。

   ![「產生覆寫」預覽](media/overrides-preview-cs.png)

1. 從下拉式功能表選取 [產生 Equals(object)]或 [產生 Equals 和 GetHashCode]。

1. 在 [選取成員]對話方塊中，選取您想要產生方法的成員：

    ![[產生覆寫] 對話方塊](media/overrides-dialog-cs.png)

    > [!TIP]
    > 您也可以選擇使用對方塊底部附近的核取方塊，從此對話方塊中產生運算子。

   系統會使用預設實作來產生 `Equals` 與 `GetHashCode` 方法。

   ![「產生方法」結果](media/overrides-result-cs.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
