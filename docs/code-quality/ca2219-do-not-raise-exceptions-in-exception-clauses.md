---
title: "CA2219： 不要引發例外狀況子句中的例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c5a4ee1d4425b3967928171648453a631aea815
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219：不要在 exception 子句中引發例外狀況
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷、 中斷|  
  
## <a name="cause"></a>原因  
 例外狀況擲回從`finally`，篩選器或 fault 子句。  
  
## <a name="rule-description"></a>規則描述  
 當例外狀況子句中引發例外狀況時，它會大幅增加偵錯困難的度。  
  
 中引發例外狀況時`finally`或 fault 子句中，新的例外狀況會隱藏作用中的例外狀況，如果有的話。 這使原始錯誤變得難以偵測及偵錯。  
  
 當篩選子句中引發例外狀況時，執行階段以無訊息模式攔截例外狀況，並會導致篩選條件評估為 false。 沒有任何方式可以分辨評估為 false，而且正在從篩選條件會擲回例外狀況篩選條件之間的差異。 這可讓您難以偵測及偵錯的篩選條件的邏輯錯誤。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此違反此規則，執行不明確引發例外狀況從`finally`，篩選器或 fault 子句。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 沒有所在例外狀況子句中引發例外狀況會提供執行的程式碼的優點的案例。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1065：不要在非預期的位置中引發例外狀況](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>請參閱  
 [設計警告](../code-quality/design-warnings.md)