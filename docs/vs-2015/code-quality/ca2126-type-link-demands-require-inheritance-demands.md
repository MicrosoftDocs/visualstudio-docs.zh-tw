---
title: CA2126：需要繼承要求的類型連結需求 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051a041c245fae55e3d4759130c145c662734aa8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544270"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126:必須同時具有類型連結要求和繼承要求
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用非密封類型受到連結要求保護，具有可覆寫的方法，且類型或方法都不會受到繼承要求的保護。

## <a name="rule-description"></a>規則描述
 方法或其宣告類型的連結要求需要方法的立即呼叫端具有指定的許可權。 方法的繼承要求需要覆寫方法才能擁有指定的許可權。 型別的繼承要求需要衍生的類別具有指定的許可權。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用與連結要求相同許可權的繼承要求來保護類型或方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2108:必須檢閱實值類型上的宣告式安全性](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112:受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122:不要間接公開具有連結要求的方法](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123:覆寫連結要求應該與基底相同](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>另請參閱
 [安全程式碼撰寫方針](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[繼承要求](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)[連結要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)[需求](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)
