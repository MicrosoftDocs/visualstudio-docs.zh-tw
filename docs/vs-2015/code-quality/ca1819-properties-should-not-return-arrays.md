---
title: CA1819：屬性不應傳回陣列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c85efc3e601eb9e0d887043c50b30587e51321e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668380"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819：屬性不應傳回陣列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Category|Microsoft。效能|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用型別中的公用或受保護屬性會傳回陣列。

## <a name="rule-description"></a>規則描述
 屬性所傳回的陣列不會受到寫入保護，即使屬性是唯讀也是一樣。 若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。 一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。 具體而言，它們可能會使用屬性做為索引屬性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將屬性設為方法，或變更屬性以傳回集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 屬性可以包含傳回陣列的屬性，但不能包含傳回集合的屬性。 您可以隱藏針對衍生自 [system.string] 之屬性（attribute）的屬性（property）所引發的警告（<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->課堂. 否則，請勿隱藏此規則的警告。

## <a name="example-violation"></a>範例違規

### <a name="description"></a>描述
 下列範例顯示違反此規則的屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>註解
 若要修正此規則的違規，請將屬性設為方法，或變更屬性以傳回集合，而不是陣列。

## <a name="change-the-property-to-a-method-example"></a>將屬性變更為方法範例

### <a name="description"></a>描述
 下列範例會藉由將屬性變更為方法來修正違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>傳回集合範例

### <a name="description"></a>描述
 下列範例會藉由變更屬性來傳回，以修正違規

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>允許使用者修改屬性

### <a name="description"></a>描述
 您可能想要允許類別的取用者修改屬性。 下列範例顯示違反此規則的讀取/寫入屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>註解
 下列範例會變更屬性來傳回 <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>，藉以修正違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)
