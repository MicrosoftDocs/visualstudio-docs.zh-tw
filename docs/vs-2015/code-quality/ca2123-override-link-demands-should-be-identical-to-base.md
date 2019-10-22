---
title: CA2123：覆寫連結要求應該與基底相同 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bec8f129c094f94ba3eb4021092c402e8263812b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660262"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123：覆寫連結要求應該與基底相同
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用型別中的公用或受保護方法會覆寫方法或實作為介面，而且不會有與介面或虛擬方法相同的[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)。

## <a name="rule-description"></a>規則描述
 這項規則會使方法符合它的基底方法，即另一個類型中的介面或虛擬方法，然後比較每個方法上的連結要求。 如果方法或基底方法有連結要求，而另一個不是，則會回報違規。

 如果違反這項規則，惡意的呼叫者只要呼叫不安全的方法，就可以略過連結要求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將相同的連結需求套用至覆寫方法或執行。 如果無法這麼做，請使用完整的要求來標示方法，或完全移除屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示此規則的各種違規。

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>請參閱
 [安全程式碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
