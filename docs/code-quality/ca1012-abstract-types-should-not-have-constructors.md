---
title: CA1012:抽象類型不應該有建構函式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd35cd7b084deb34b23b49ebc04517733c5478c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006774"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012:抽象類型不應該有建構函式

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用類型是抽象的並且具有公用建構函式。

## <a name="rule-description"></a>規則描述
 只有衍生類型 (Derived Type) 可以呼叫抽象類型上的建構函式。 因為公用建構函式會建立類型的執行個體，而且您無法建立抽象類型的執行個體，因此具有公用建構函式的抽象類型設計不正確。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，讓受保護的建構函式或是未宣告為抽象型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 抽象型別具有公用建構函式。

## <a name="example"></a>範例
 下列範例包含違反此規則的抽象型別。

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>範例
 下列範例會藉由變更從建構函式的協助工具修正上述違規`public`至`protected`。

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]