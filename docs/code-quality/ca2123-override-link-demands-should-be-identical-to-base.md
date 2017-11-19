---
title: "CA2123： 覆寫連結要求應該與基底相同 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e39d278588d8fbce5bc9a7ee77141a56341e8f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123：覆寫連結要求應該與基底相同
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或保護方法的公用類型中覆寫的方法或實作介面，而且沒有相同[連結要求](/dotnet/framework/misc/link-demands)與介面或虛擬方法。  
  
## <a name="rule-description"></a>規則描述  
 這項規則會使方法符合它的基底方法，即另一個類型中的介面或虛擬方法，然後比較每個方法上的連結要求。 如果在方法或基底的方法有連結需求，而其他則不會報告違反。  
  
 如果違反這項規則，則惡意呼叫端可以呼叫略過連結要求只是不安全的方法。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，套用相同的連結要求來覆寫方法或實作。 如果不可行，標記的方法用完整的要求，或完全移除屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會示範各種違反此規則。  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)   
 [連結要求](/dotnet/framework/misc/link-demands)