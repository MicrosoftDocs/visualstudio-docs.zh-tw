---
title: "CA2126： 類型連結要求需要繼承要求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 254fd15f97afe69f927bb8a1aae1954105776641
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126：必須同時具有類型連結要求和繼承要求
|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用 unsealed 的類型受到連結要求，具有可覆寫的方法和類型或方法都不以繼承要求保護。  
  
## <a name="rule-description"></a>規則描述  
 方法或其宣告類型的連結要求需要立即方法的呼叫端擁有指定的權限。 方法的繼承要求需要覆寫方法具有指定的權限。 類型的繼承要求需要衍生的類別具有的指定權限。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，安全類型或方法，以繼承要求相同的權限與連結要求。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2108：必須檢查實值型別上的宣告式安全性](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112：受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122：不要間接公開具有連結要求的方法](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123：覆寫連結要求應該與基底相同](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)   
 [繼承要求](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [連結要求](/dotnet/framework/misc/link-demands)   
 [要求](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48)