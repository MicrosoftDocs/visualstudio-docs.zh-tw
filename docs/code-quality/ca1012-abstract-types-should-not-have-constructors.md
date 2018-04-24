---
title: CA1012：抽象類型不應具有建構函式
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf4f29a11a831bd5b7d4860dd15698922df3a2c6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012：抽象類型不應具有建構函式
|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用類型是抽象的而且具有公用建構函式。

## <a name="rule-description"></a>規則描述
 只有衍生類型 (Derived Type) 可以呼叫抽象類型上的建構函式。 因為公用建構函式會建立類型的執行個體，而且您無法建立抽象類型的執行個體，因此具有公用建構函式的抽象類型設計不正確。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請讓受保護的建構函式，或未宣告為抽象類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 抽象類型具有公用建構函式。

## <a name="example"></a>範例
 下列範例包含違反此規則的抽象型別。

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>範例
 下列範例會藉由變更從建構函式的存取範圍修正上述違規`public`至`protected`。

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]