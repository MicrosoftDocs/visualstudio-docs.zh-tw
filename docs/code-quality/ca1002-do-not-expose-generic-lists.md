---
title: CA1002：不要公開泛型清單
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016b9f72567f6ff70b19bfa9e781e0f0d14cb702
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549348"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002：不要公開泛型清單
|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別含有的是外部可見成員<xref:System.Collections.Generic.List%601?displayProperty=fullName>類型，會傳回<xref:System.Collections.Generic.List%601?displayProperty=fullName>型別或其簽章包含<xref:System.Collections.Generic.List%601?displayProperty=fullName>參數。

## <a name="rule-description"></a>規則描述
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 是泛型集合，專為效能和不繼承。 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 不包含可讓您更輕鬆地變更繼承的類別行為的虛擬成員。 下列的泛型集合專為繼承，而且應該公開而不是<xref:System.Collections.Generic.List%601?displayProperty=fullName>。

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更<xref:System.Collections.Generic.List%601?displayProperty=fullName>至其中一個泛型集合，專為繼承的型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告，除非將會引發此警告的組件不是用來重複使用程式庫。 比方說，它會安全地隱藏這個警告，效能微調應用程式中的泛型清單使用而獲得效能優勢。

## <a name="related-rules"></a>相關的規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](/dotnet/csharp/programming-guide/generics/index)