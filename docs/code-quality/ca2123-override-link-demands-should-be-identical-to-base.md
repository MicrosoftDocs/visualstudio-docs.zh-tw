---
title: CA2123：覆寫連結要求應該與基底相同
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 340b0e7deb12d4568a76d4871eabd49641926dcb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920358"
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
 [安全編碼方針](/dotnet/standard/security/secure-coding-guidelines)[連結要求](/dotnet/framework/misc/link-demands)