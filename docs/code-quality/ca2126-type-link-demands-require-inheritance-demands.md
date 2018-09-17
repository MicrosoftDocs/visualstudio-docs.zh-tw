---
title: CA2126：必須同時具有類型連結要求和繼承要求
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82fe9045173e65b24204a3b04e12b6a7f655c651
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548393"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126：必須同時具有類型連結要求和繼承要求

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用 unsealed 的類型受到連結要求，覆寫的方法，而且型別和方法都不會受到保護以繼承要求。

## <a name="rule-description"></a>規則描述
 方法或其宣告類型的連結要求需要立即方法的呼叫端擁有指定的權限。 在方法上的繼承要求需要覆寫的方法，將指定的權限。 繼承要求的型別上需要有指定的權限的衍生類別。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，安全的型別或具有繼承要求提供相同的權限，為連結要求的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2108：必須檢查實值型別上的宣告式安全性](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112：受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122：不要間接公開具有連結要求的方法](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123：覆寫連結要求應該與基底相同](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](/dotnet/standard/security/secure-coding-guidelines)
- [連結要求](/dotnet/framework/misc/link-demands)