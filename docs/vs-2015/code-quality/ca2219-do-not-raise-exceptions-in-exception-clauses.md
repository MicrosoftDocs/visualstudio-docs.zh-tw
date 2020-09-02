---
title: CA2219：不要在 exception 子句中引發例外狀況 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538524"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219:不要在 exception 子句中引發例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|類別|Microsoft. 使用量|
|中斷變更|非中斷、中斷|

## <a name="cause"></a>原因
 從 `finally` 、filter 或 fault 子句擲回例外狀況。

## <a name="rule-description"></a>規則描述
 例外狀況子句中引發例外狀況時，會大幅增加偵錯工具的困難。

 當或 fault 子句中引發例外狀況時 `finally` ，新的例外狀況會隱藏作用中的例外狀況（如果有的話）。 這會讓原始錯誤難以偵測和偵測。

 在篩選子句中引發例外狀況時，執行時間會以無訊息方式捕捉例外狀況，並讓篩選準則評估為 false。 沒有任何方法可分辨評估為 false 的篩選與從篩選擲回的例外狀況之間的差異。 這使得偵測和偵測篩選器邏輯中的錯誤變得很困難。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請不要明確地從 `finally` 、filter 或 fault 子句引發例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 在例外狀況子句中引發例外狀況的情況下，不會提供執行中程式碼的優點。

## <a name="related-rules"></a>相關規則
 [CA1065:不要在非預期的位置中引發例外狀況](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>另請參閱
 [設計警告](../code-quality/design-warnings.md)
