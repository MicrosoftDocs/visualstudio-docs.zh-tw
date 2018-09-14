---
title: CA1004：泛型方法應該提供類型參數
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b282545d04c82efb44ed87d21ddf66ee73ab77af
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550930"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004：泛型方法應該提供類型參數

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的泛型方法的參數簽章不包含對應至方法的所有型別參數的類型。

## <a name="rule-description"></a>規則描述
 推斷是指如何利用傳遞到泛型方法的引數類型，而不是利用類型引數的明確規格，來決定泛型方法的類型引數。 若要啟用推斷，泛型方法的參數簽章必須包含與方法之類型參數具有相同類型的參數。 在上述情形中，不必指定類型引數。 當您使用推斷所有類型參數時，呼叫泛型和非泛型執行個體方法的語法完全相同。 這可簡化泛型方法的可用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更設計，使參數簽章包含每個類型參數的方法相同的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 提供了容易了解和使用的語法中的泛型減少時間，才能了解，並增加新的程式庫的採用率。

## <a name="example"></a>範例
 下列範例顯示呼叫兩個泛型方法的語法。 型別引數`InferredTypeArgument`會推斷的型別引數和`NotInferredTypeArgument`必須明確指定。

 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](/dotnet/csharp/programming-guide/generics/index)