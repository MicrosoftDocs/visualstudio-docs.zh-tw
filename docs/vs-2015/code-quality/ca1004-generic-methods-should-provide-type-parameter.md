---
title: CA1004：泛型方法應該提供類型參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a7c64337af94f9e88944fd15480f4b7ce1e2cb08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655259"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004：泛型方法應該提供類型參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見泛型方法的參數簽章不包含對應至方法之所有型別參數的類型。

## <a name="rule-description"></a>規則描述
 推斷是指如何利用傳遞到泛型方法的引數類型，而不是利用型別引數的明確規格，來決定泛型方法的型別引數。 若要啟用推斷，泛型方法的參數簽章必須包含與方法之型別參數具有相同類型的參數。 在上述情形中，不必指定類型引數。 當您對所有型別參數使用推斷時，呼叫泛型和非泛型實例方法的語法完全相同。 這可簡化泛型方法的可用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請變更設計，讓參數簽章針對方法的每個類型參數包含相同的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 以易於瞭解和使用的語法提供泛型，可減少學習及增加新程式庫採用率所需的時間。

## <a name="example"></a>範例
 下列範例顯示呼叫兩個泛型方法的語法。 會推斷 `InferredTypeArgument` 的型別引數，而且必須明確指定 `NotInferredTypeArgument` 的型別引數。

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)