---
title: "產生 Equals 與 GetHashCode 方法覆寫 - 程式碼產生 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>使用 C# 來產生 Equals 與 GetHashCode 方法覆寫 #

**功能：**讓您產生 **Equals** 與 **GetHashCode** 方法。

**時機：**當您有某個類型，而該類型代表應該由某些欄位而不是由記憶體中之物件位置比較的「值」時，請產生這些覆寫。

**原因：**如果您要實作值類型，便應該考慮覆寫 Equals 方法，以獲得比在 ValueType 上實作預設 Equals 方法更好的效能。

如果您要實作參考類型，當該類型看似基底類型 (例如 Point、String、BigNumber 等) 時，便應該考慮覆寫 Equals 方法。

覆寫 GetHashCode 方法以允許類型在雜湊表中正確運作。 如需更多指引，請參閱[等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)。

**做法：**

1. 將游標放在類型宣告中。

   ![醒目標示的程式碼](media/overrides-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生 Equals(object)] 或 [產生 Equals 與 GetHashCode]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生 Equals(object)] 或 [產生 Equals 與 GetHashCode]。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有類型宣告的行上，此圖示就會出現在左邊界上。

   ![「產生覆寫」預覽](media/overrides-preview-cs.png)

1. 選取您要為其產生覆寫方法的成員：

    ![[產生覆寫] 對話方塊](media/overrides-dialog-cs.png)

    > [!TIP]
    > 您也可以選擇從此對話方塊中，使用成員清單底下的核取方塊來產生運算子。

1. 系統將會使用自動預設實作來產生 Equals 與 GetHashCode 覆寫。

   ![「產生方法」結果](media/overrides-result-cs.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)
