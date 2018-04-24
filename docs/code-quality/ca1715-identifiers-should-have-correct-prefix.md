---
title: CA1715：識別項名稱應該使用正確的前置字元
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b4ddef7b6a9ae7eafb6c169ec9e07e89e20fc6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715：識別項名稱應該使用正確的前置字元
|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|分類|Microsoft.Naming|
|中斷變更|中斷-引發介面上時。<br /><br /> 非中斷-產生泛型型別參數時。|

## <a name="cause"></a>原因
 外部可見的介面名稱不開頭大寫 'I'。

 -或-

 外部可見類型或方法上泛型型別參數名稱開頭不大寫 ' T '。

## <a name="rule-description"></a>規則描述
 依照慣例，具有特定前置詞開頭的特定程式設計項目名稱。

 介面名稱必須以大寫 'I' 後面接著另一個大寫字母開頭。 此規則會回報介面名稱，例如 'MyInterface' 和 'IsolatedInterface' 的違規。

 泛型型別參數名稱開頭應該以大寫 'T' 和 （選擇性） 後面跟著另一個大寫字母。 此規則會回報的泛型型別參數名稱，例如 'V' 和 'Type' 的違規。

 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。

## <a name="how-to-fix-violations"></a>如何修正違規
 重新命名識別項，以便正確前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 **下列範例顯示命名錯誤介面。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>範例
 **下列範例會修正上述違規加與 'I' 的介面。**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>範例
 **下列範例顯示命名錯誤的泛型型別參數。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>範例
 **下列範例會藉由前置詞的泛型型別參數 ' T 修正上述違規 '。**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1722：識別項名稱不應該使用不正確的前置字元](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)