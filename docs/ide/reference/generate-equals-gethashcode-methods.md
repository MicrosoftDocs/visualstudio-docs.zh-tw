---
title: 在 Visual Studio 中產生 C# Equals 與 GetHashCode 方法覆寫 | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: conceptual
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3768659ce6c4e52c9e4f6473207fc74513797f17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>在 Visual Studio 中產生 Equals 與 GetHashCode 方法覆寫

此程式碼產生適用於：

- C#

**功能：**讓您產生 **Equals** 與 **GetHashCode** 方法。

**時機：**當您有某個類型應由一或多個欄位比對，而不是由記憶體中的物件位置比對時，請產生這些覆寫。

**原因：**

- 如果您要實作實值型別，便應該考慮覆寫 **Equals** 方法，以獲得比在 ValueType 上實作預設 Equals 方法更好的效能。

- 如果您要實作參考型別，當該類型看似基底類型 (例如 Point、String、BigNumber 等) 時，便應該考慮覆寫 **Equals** 方法。

- 覆寫 **GetHashCode** 方法以允許類型在雜湊表中正確運作。 如需更多指引，請參閱[等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)。

## <a name="how-to"></a>操作說明

1. 將游標放在類型宣告中。

   ![醒目標示的程式碼](media/overrides-highlight-cs.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
     - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
     - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。
     - 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有類型宣告的行上，此圖示就會出現在左邊界上。

   ![「產生覆寫」預覽](media/overrides-preview-cs.png)

1. 從下拉式功能表選取 [產生 Equals(object)]或 [產生 Equals 和 GetHashCode]。

1. 在 [選取成員]對話方塊中，選取您想要產生方法的成員：

    ![[產生覆寫] 對話方塊](media/overrides-dialog-cs.png)

    > [!TIP]
    > 您也可以選擇從此對話方塊中，使用成員清單底下的核取方塊來產生運算子。

   系統會使用預設實作來產生 Equals 與 GetHashCode 覆寫。

   ![「產生方法」結果](media/overrides-result-cs.png)

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
