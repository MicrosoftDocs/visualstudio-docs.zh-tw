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
ms.openlocfilehash: e7a96c95313ffee82448e3485c90868c8103814a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539798"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004：泛型方法應該提供類型參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見泛型方法的參數簽章不包含對應至方法之所有型別參數的類型。

## <a name="rule-description"></a>規則描述
 推斷是指如何利用傳遞到泛型方法的引數類型，而不是利用型別引數的明確規格，來決定泛型方法的型別引數。 若要啟用推斷，泛型方法的參數簽章必須包含與方法之型別參數具有相同類型的參數。 在上述情形中，不必指定類型引數。 當您針對所有類型參數使用推斷時，呼叫泛型和非泛型實例方法的語法相同。 這可簡化泛型方法的使用性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更設計，讓參數簽章針對方法的每個類型參數包含相同的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 以易於瞭解的語法提供泛型，使用可減少學習和提高新程式庫採用率所需的時間。

## <a name="example"></a>範例
 下列範例顯示呼叫兩個泛型方法的語法。 會推斷的型別引數 `InferredTypeArgument` ，而且必須明確指定的型別引數 `NotInferredTypeArgument` 。

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007:建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)