---
title: 將 Foreach 迴圈轉換為 LINQ
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 462a9624809d2dccfe68bb2e016dda6739d9c2e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936843"
---
# <a name="convert-a-foreach-loop-to-linq"></a>將 Foreach 迴圈轉換為 LINQ

此重構適用於：

- C#

事項 **：** 可讓您輕鬆地將使用 IEnumerable 的 *foreach* 迴圈轉換成 linq 查詢或 linq 呼叫表單 (也稱為 linq 方法) 。

時機 **：** 您有一個使用 IEnumerable 的 foreach 迴圈，而您想要該迴圈讀取為 LINQ 查詢。

**原因：** 您偏好使用 LINQ 語法，而不是 foreach 迴圈。 [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) 會在 C# 中將查詢設為第一類語言建構。 LINQ 可以減少檔案中的程式碼數量，讓程式碼更容易閱讀，並允許不同資料來源具有類似的查詢運算式模式。

> [!NOTE]
> LINQ 語法的效率通常比 Foreach 迴圈低。 當您使用 LINQ 來提高程式碼的可讀性時，最好注意可能出現的任何效能影響。

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>將 Foreach 迴圈轉換為 LINQ 重構

1. 將游標放在 `foreach` 關鍵字中。

    ![使用 IEnumerable 範例的 Foreach](media/convert-foreach-to-LINQ.png)

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   ![轉換為 LINQ 功能表範例](media/convert-foreach-to-LINQ-codefix.png)

3. 選取 [ **轉換成 linq** ] 或 [ **轉換成 linq (呼叫表單)**。

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
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
