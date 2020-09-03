---
title: CA1005：避免在泛型型別上有過度的參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56c69badf76a05351b37a7c8a41a9cacf54f9974
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539720"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005：避免在泛型類型上包含過多參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的泛型型別具有兩個以上的型別參數。

## <a name="rule-description"></a>規則描述
 泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 在某些情況下，通常會使用一個類型參數（如同 `List<T>` ），而且在某些情況下，有兩個型別參數，如下所示 `Dictionary<TKey, TValue>` 。 如果有兩個以上的型別參數，則對大部分的使用者而言，這個困難就變得太大了 (例如， `TooManyTypeParameters<T, K, V>` c # 或 `TooManyTypeParameters(Of T, K, V)` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將設計變更為使用不超過兩個型別參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非設計絕對需要兩個以上的類型參數，否則請勿隱藏此規則的警告。 以易於瞭解的語法提供泛型，使用可減少學習和提高新程式庫採用率所需的時間。

## <a name="related-rules"></a>相關規則
 [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007:建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
