---
title: "產生 Equals 和 GetHashCode 方法覆寫-產生程式碼 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>產生 Equals 和 GetHashCode 方法覆寫在 C# 中 #

**項目：**可讓您產生**等於**和**GetHashCode**方法。

**當：**產生這些覆寫，當您有代表 「 值 」 應該比較欄位，而不是在記憶體中物件位置的類型。

**原因：**如果您正在實作實值類型，您應該考慮覆寫 Equals 方法，可以提升的效能上的 ValueType Equals 方法的預設實作。

如果您實作的參考類型，您應該考慮覆寫 Equals 方法，如果您的型別看起來像基底類型，例如點、 字串、 BigNumber，等等。

覆寫 GetHashCode 方法，以允許正常運作，雜湊表中的類型。 閱讀更多指導[等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)。

**如何：**

1. 將游標放在您的型別宣告。

   ![反白顯示的程式碼](media/overrides_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**產生 Equals(object)**或**產生 Equals 和 GetHashCode**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**產生 Equals(object)**或**產生 Equals 和 GetHashCode**從預覽視窗快顯視窗。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經列中利用的型別宣告，會出現在左邊界的圖示。

   ![產生的覆寫預覽](media/overrides_preview.png)

1. 選取您想要產生的覆寫方法的成員：

    ![產生的覆寫 對話方塊](media/overrides_dialog.png)

    > [!TIP]
    > 您也可以選擇在這個對話產生運算子，使用 [成員] 清單下方的核取方塊。

1. Equals 和 GetHashCode 覆寫會產生含有自動的預設實作。

   ![產生方法結果](media/overrides_result.png)

## <a name="see-also"></a>請參閱

[程式碼產生 (C#)](../code-generation-csharp.md)  
[預覽變更](../../ide/preview-changes.md)
