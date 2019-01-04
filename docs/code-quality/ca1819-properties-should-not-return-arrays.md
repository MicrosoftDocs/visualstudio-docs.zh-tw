---
title: CA1819:屬性不應該傳回陣列
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6159d6b9a2d8d3dc02cd5f0690f3b1360b4461fd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949452"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819:屬性不應該傳回陣列

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|分類|Microsoft.Performance|
|中斷變更|中斷|

## <a name="cause"></a>原因

公用類型中的公用或受保護的屬性會傳回陣列。

## <a name="rule-description"></a>規則描述

屬性所傳回的陣列不是寫入保護，即使屬性是唯讀的。 若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。 一般而言，使用者不了解呼叫這類屬性的不良效能影響。 具體來說，它們可能會使用屬性做為索引的屬性。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將屬性設為方法或是變更要傳回集合的屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以隱藏的屬性衍生自屬性，就會引發警告<xref:System.Attribute>類別。 屬性可以包含傳回陣列的屬性，但不能包含傳回集合的屬性。

您可以隱藏警告，如果屬性是屬於[資料傳輸物件 (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10))類別。

否則，請勿隱藏此規則的警告。

## <a name="example-violation"></a>範例違規

下列範例顯示違反此規則的屬性：

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

若要修正此規則的違規情形，將屬性設為方法或是變更要傳回的集合，而不是陣列的屬性。

### <a name="change-the-property-to-a-method"></a>將屬性變更為方法

下列範例會藉由屬性變更為方法修正違規：

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>變更要傳回集合的屬性

下列範例會藉由變更要傳回之屬性修正違規<xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>允許使用者修改屬性

您可能想要讓取用者類別，來修改的屬性。 下列範例顯示違反此規則的讀取/寫入屬性：

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

下列範例會藉由變更要傳回之屬性修正違規<xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>相關的規則

- [CA1024:在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)