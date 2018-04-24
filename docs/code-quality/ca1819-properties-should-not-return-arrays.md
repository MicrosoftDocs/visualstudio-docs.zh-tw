---
title: CA1819：屬性不應傳回陣列
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: 8f98e92174d7f01c6adf174ef5ff27e68ca406ae
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819：屬性不應傳回陣列
|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|分類|Microsoft.Performance|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的屬性中的公用型別傳回陣列。

## <a name="rule-description"></a>規則描述
 所傳回的陣列會不防寫保護，即使屬性是唯讀的。 若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。 一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。 具體而言，它們可能會使用屬性做為索引的屬性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將屬性設為方法，或變更以傳回集合的屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 屬性可以包含傳回陣列的內容，但不能包含傳回集合的屬性。 您可以隱藏衍生自屬性的屬性，就會引發警告<xref:System.Attribute>類別。 否則，請勿隱藏此規則的警告。

## <a name="example-violation"></a>範例違規

### <a name="description"></a>描述
 下列範例會示範違反此規則的屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>註解
 若要修正此規則的違規情形，請將屬性設為方法，或變更要傳回的集合，而非陣列的屬性。

## <a name="change-the-property-to-a-method-example"></a>將屬性變更為方法範例

### <a name="description"></a>描述
 下列範例會修正的屬性變更為方法的違規。

### <a name="code"></a>程式碼
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>傳回集合的範例

### <a name="description"></a>描述
 下列範例會藉由變更要傳回之屬性修正違規

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>允許使用者修改屬性

### <a name="description"></a>描述
 您可能想要允許取用者的類別來修改的屬性。 下列範例會示範違反此規則的讀取/寫入屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>註解
 下列範例會藉由變更要傳回之屬性修正違規<xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>。

### <a name="code"></a>程式碼
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)