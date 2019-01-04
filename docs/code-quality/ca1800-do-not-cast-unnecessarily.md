---
title: CA1800:不要執行不必要的轉換
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 1ef6e73812a63fdc4cc4392621ab49b279a32d18
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822025"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800:不要執行不必要的轉換

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
方法會執行其中一個引數或區域變數重複轉型。

此規則的完整分析，測試的組件必須先建置使用偵錯資訊，以及相關聯的程式資料庫 (.pdb) 檔案必須能夠使用。

## <a name="rule-description"></a>規則描述
重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 對於明確重複的轉換作業，轉型將結果儲存在本機變數，並使用本機變數，而不是重複轉型作業。

如果 C#`is`運算子用來測試是否轉型成功執行實際的轉型之前, 測試的結果，請考慮`as`運算子改。 這會提供相同的功能，而不由執行隱含轉型作業`is`運算子。 或者，您也可以在 C# 7.0 和更新版本中，使用`is`運算子搭配[模式比對](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)檢查型別轉換，並在一個步驟中轉換該類型的運算式給變數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，修改的方法實作的型別轉換作業數目降到最低。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 則隱藏這項規則的警告，或完全忽略規則如果效能不成問題。

## <a name="examples"></a>範例
 下列範例示範的方法，使用 C# 中違反規則`is`運算子。 第二種方法來取代符合規則`is`運算子的結果對測試加`as`運算子，就會減少每個反覆項目至其中的兩個型別轉換作業的數目。 第三個方法也會滿足規則使用 `is`具有[模式比對](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)以建立所需類型的變數，如果類型轉換會成功。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 下列範例示範的方法中， `start_Click`，具有多個重複的明確轉型規則和方法，這會違反`reset_Click`，這會滿足規則，藉由將轉換儲存在本機變數。

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>另請參閱

- [as （C# 參考）](/dotnet/csharp/language-reference/keywords/as)
- [is （C# 參考）](/dotnet/csharp/language-reference/keywords/is)