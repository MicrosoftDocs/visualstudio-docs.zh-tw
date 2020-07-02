---
title: CA2219：不要在例外狀況子句中引發例外狀況 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538524"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219:不要在 exception 子句中引發例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|類別|Microsoft。使用方式|
|中斷變更|不中斷、中斷|

## <a name="cause"></a>原因
 例外狀況是從 `finally` 、篩選或錯誤子句擲出。

## <a name="rule-description"></a>規則描述
 在 exception 子句中引發例外狀況時，它會大幅增加了偵錯工具的困難度。

 當或 fault 子句中引發例外狀況時 `finally` ，新的例外狀況會隱藏作用中的例外狀況（如果有的話）。 這會讓原始錯誤難以偵測和 debug。

 在篩選子句中引發例外狀況時，執行時間會以無訊息方式攔截例外狀況，並讓篩選準則評估為 false。 沒有任何方法可以分辨評估為 false 的篩選準則與從篩選準則擲回的例外狀況之間的差異。 這使得偵測和偵測篩選器邏輯中的錯誤變得很困難。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請不要從 `finally` 、篩選或錯誤子句明確地引發例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 在例外狀況子句中引發例外狀況的情況下，不會提供執行程式碼的好處。

## <a name="related-rules"></a>相關規則
 [CA1065:不要在非預期的位置中引發例外狀況](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>另請參閱
 [設計警告](../code-quality/design-warnings.md)
