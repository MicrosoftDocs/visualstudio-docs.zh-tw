---
title: CA1007:建議在適當時使用泛型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0d7783bea936b04fcb600563dadea6a65ac5ef5e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236525"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007:建議在適當時使用泛型

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因
外部可見的方法包含型<xref:System.Object?displayProperty=fullName>別的參考參數，而且包含的元件目標 .NET Framework 2.0。

## <a name="rule-description"></a>規則描述
參考參數是使用`ref` （`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]）關鍵字來修改的參數。 為參考參數提供的引數類型必須完全符合參考參數類型。 若要使用衍生自參考參數類型的類型，必須先轉換類型，並將其指派給參考參數類型的變數。 使用泛型方法可讓所有類型（受限於條件約束）傳遞至方法，而不需要先將類型轉換為參考參數類型。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請將方法設為泛型， <xref:System.Object>並使用型別參數來取代參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示同時實作為非泛型和泛型方法的一般用途交換常式。 請注意，相較于非泛型方法，使用泛型方法來交換字串的效率如何。

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>相關規則
[CA1005避免在泛型型別上有過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010集合應執行泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006不要在成員簽章中嵌套泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 必須使用一般事件處理常式實例](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>另請參閱
[泛型](/dotnet/csharp/programming-guide/generics/index)