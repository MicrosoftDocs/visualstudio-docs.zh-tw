---
title: CA1014：使用 CLSCompliantAttribute 標記元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c6dc131a2bb5f0c54943213fbb42561a0c72d95c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545466"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014:組件必須標記 CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|類別|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 元件未套用 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 屬性。

## <a name="rule-description"></a>規則描述
 Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會指示所有元件都明確指出符合 CLS 規範 <xref:System.CLSCompliantAttribute> 。 如果屬性不存在於元件上，則元件不符合規範。

 符合 CLS 標準的元件可能會包含不符合規範的類型或類型成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將屬性新增至元件。 您應該判斷哪些類型或類型成員不符合規範，並將這些元素標示為，而不是將整個元件標記為不相容。 可能的話，您應該為不相容的成員提供符合 CLS 規範的替代方法，讓最廣泛的可能物件可以存取元件的所有功能。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 如果您不想要讓元件符合規範，請套用屬性，並將其值設定為 `false` 。

## <a name="example"></a>範例
 下列範例會顯示已套用屬性的元件，其會將它宣告為 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 符合 CLS 標準。

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>[語言獨立性和與語言無關的元件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
