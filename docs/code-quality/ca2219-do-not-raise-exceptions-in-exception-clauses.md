---
title: CA2219:不要在 exception 子句中引發例外狀況
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a644cf3dc934676a14f1c5c59a6582fcd45ae7d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941149"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219:不要在 exception 子句中引發例外狀況

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|分類|Microsoft.Usage|
|中斷變更|非中斷、 中斷|

## <a name="cause"></a>原因
 發生例外狀況從`finally`，篩選或 fault 子句。

## <a name="rule-description"></a>規則描述
 當例外狀況子句中引發例外狀況時，它會大幅增加偵錯困難的度。

 在引發例外狀況時`finally`或 fault 子句中，新的例外狀況會隱藏作用中的例外狀況，如果有的話。 這可讓原錯誤更難以偵測及偵錯。

 Filter 子句中引發例外狀況時，執行階段以無訊息模式攔截到例外狀況，並會導致篩選條件評估為 false。 沒有任何方法來告知的篩選條件評估為 false，並從篩選條件擲回之例外狀況的差異。 這可讓您難以偵測及偵錯中篩選條件的邏輯錯誤。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此違規的此規則，不要明確地引發的例外狀況`finally`，篩選或 fault 子句。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這項規則的警告。 沒有在其下的例外狀況子句中引發例外狀況提供執行的程式碼的好處的案例。

## <a name="related-rules"></a>相關的規則
 [CA1065:不會引發非預期的位置中的例外狀況](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>另請參閱
 [設計警告](../code-quality/design-warnings.md)