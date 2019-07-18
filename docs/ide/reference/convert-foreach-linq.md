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
ms.openlocfilehash: 7893ed676372cce94d883353139de91ef639aeb0
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531853"
---
# <a name="convert-a-foreach-loop-to-linq"></a>將 Foreach 迴圈轉換為 LINQ

此重構適用於：

- C#

**功能：** 可讓您將使用 IEnumerables 的 *Foreach* 迴圈，輕鬆地轉換為 LINQ 查詢或 LINQ 呼叫表單 (也稱為 LINQ 方法)。

**時機：** 您擁有使用 IEnumerables 的 Foreach 迴圈，且您想要該迴圈讀取為 LINQ 查詢。

**原因：** 您更喜歡使用 LINQ 語法，而不是 Foreach 迴圈。 [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) 會在 C# 中將查詢設為第一類語言建構。 LINQ 可以減少檔案中的程式碼數量，讓程式碼更容易閱讀，並允許不同資料來源具有類似的查詢運算式模式。

> [!NOTE]
> LINQ 語法的效率通常比 Foreach 迴圈低。 當您使用 LINQ 來提高程式碼的可讀性時，最好注意可能出現的任何效能影響。

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>將 Foreach 迴圈轉換為 LINQ 重構

1. 將游標放在 `foreach` 關鍵字中。

    ![使用 IEnumerable 範例的 Foreach](media/convert-foreach-to-LINQ.png)

2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![轉換為 LINQ 功能表範例](media/convert-foreach-to-LINQ-codefix.png)

3. 選取 [轉換至 LINQ] 或 [轉換為 Linq (呼叫表單)]。

   ![LINQ 查詢結果範例](media/convert-foreach-to-LINQ-result.png)

   ![LINQ 呼叫表單結果範例](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>範例程式碼

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [[預覽變更] 視窗](../../ide/preview-changes.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)
