---
title: 將 Foreach 迴圈轉換為 LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eadad8fdbec990607450b374a32758547194f734
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160270"
---
# <a name="convert-foreach-loop-to-linq"></a>將 Foreach 迴圈轉換為 LINQ

此重構適用於：

- C#

**功能：** 可讓您使用 IEnumerables 輕鬆將 foreach 迴圈轉換為 LINQ 查詢或 LINQ 呼叫表單 (也稱為 LINQ 方法)。

**時機：** 當您擁有的 foreach 迴圈會使用您想要讀取為 LINQ 查詢的 IEnumerable。

**原因：** 有時候使用者可能會偏好使用 LINQ 語法，而不是 foreach 迴圈。 [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) 會在 C# 中將查詢設為第一類語言建構。 LINQ 可以減少檔案中的程式碼數量，讓其更容易閱讀，並允許不同資料來源具有類似的查詢運算式模式。

> [!NOTE]
> LINQ 語法的效能通常比 foreach 迴圈較低。 在使用 LINQ 來改善程式碼的可讀性時，建議您了解可能導致的任何效能權衡。

## <a name="convert-foreach-loop-to-linq-refactoring"></a>將 foreach 迴圈轉換為 LINQ 重構

1. 將游標放在 `foreach` 關鍵字中。

    ![使用 IEnumerable 的 Foreach](media/convert-foreach-to-LINQ.png)

2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![轉換為 LINQ 功能表](media/convert-foreach-to-LINQ-codefix.png)

3. 選取 [轉換成 LINQ] 或 [轉換成 Linq (呼叫表單)]

   ![LINQ 查詢結果](media/convert-foreach-to-LINQ-result.png)
   
   ![LINQ 呼叫表單結果](media/convert-foreach-to-LINQ-callform-result.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../../ide/visual-studio-2017-for-dotnet-developers.md)