---
title: CA1804:必須移除未使用的區域變數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f567fa1d1f793395532efac5991b01c5087b638a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908526"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804:必須移除未使用的區域變數

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法的本機變數宣告，但未使用的變數，但可能收件者在指派陳述式。 此規則的分析，請測試的組件必須以偵錯資訊建置，並必須可以使用相關聯的程式資料庫 (.pdb) 檔案。

## <a name="rule-description"></a>規則描述
 未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除，或使用本機變數。 請注意，C# 編譯器隨附[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]移除未使用的本機變數時`optimize`啟用選項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果變數是由編譯器發出，則隱藏此規則的警告。 也很安全隱藏這項規則的警告，或停用規則，如果效能和程式碼維護不是主要的考量。

## <a name="example"></a>範例
 下列範例會示範幾個未使用的本機變數。

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1809:避免過多區域變數](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801： 必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)