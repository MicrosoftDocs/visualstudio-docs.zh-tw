---
title: CA1800：請勿執行不必要的轉型
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 34c03adb8ff34d3590ed93264d77536c4cdff080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800：請勿執行不必要的轉型
|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|分類|Microsoft.Performance|
|中斷變更|非中斷|

## <a name="cause"></a>原因
方法會在其中一個引數或本機變數上執行重複轉型。

此規則所完成的分析，請使用偵錯資訊，也必須建置測試的組件和相關聯的程式資料庫 (.pdb) 檔案必須能夠使用。

## <a name="rule-description"></a>規則描述
重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 明確重複轉型作業轉型將結果儲存在本機變數，並使用此區域變數，而不是重複轉型作業。

如果 C#`is`運算子用來測試是否轉型將會成功，實際的轉換執行之前，測試結果，請考慮`as`運算子改為。 這會提供相同的功能，而不會執行的隱含轉型作業`is`運算子。 或者，在 C# 7.0 和更新版本，使用`is`運算子搭配[模式比對](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)檢查型別轉換，並在該類型的變數將運算式轉換成以一個步驟。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請修改方法實作中的轉換作業數目降至最低。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果效能不重要的考量，就會隱藏此規則的警告，或完整地忽略此規則的安全。

## <a name="examples"></a>範例
 下列範例顯示使用 C# 違反規則的方法`is`運算子。 第二種方法來取代符合規則`is`運算子與測試的結果`as`運算子，就會減少每個反覆項目從一到兩個型別轉換作業的數目。 第三個方法也會滿足規則使用`is`與[模式比對](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is)建立所需類型的變數，如果型別轉換會成功。

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 下列範例會示範一種方法， `start_Click`，具有多個重複的明確轉型的違反規則和方法， `reset_Click`，符合規則的本機變數中儲存轉型。

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>另請參閱
[（C# 參考） 為](/dotnet/csharp/language-reference/keywords/as)
[（C# 參考）](/dotnet/csharp/language-reference/keywords/is)