---
title: CA1014:組件必須標記 CLSCompliantAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 387eb464959fba522e31f9586998335cb306d844
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236318"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014:組件必須標記 CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因
元件未<xref:System.CLSCompliantAttribute?displayProperty=fullName>套用屬性。

## <a name="rule-description"></a>規則描述
Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會指示所有元件都明確指出符合<xref:System.CLSCompliantAttribute>CLS 規範。 如果屬性不存在於元件上，則元件不符合規範。

符合 CLS 標準的元件可能會包含不符合規範的類型或類型成員。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請將屬性新增至元件。 您應該判斷哪些類型或類型成員不符合規範，並將這些元素標示為，而不是將整個元件標記為不相容。 可能的話，您應該為不相容的成員提供符合 CLS 規範的替代方法，讓最廣泛的可能物件可以存取元件的所有功能。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 如果您不想要讓元件符合規範，請套用屬性，並將其值設定`false`為。

## <a name="example"></a>範例
下列範例會顯示已套用屬性的元件<xref:System.CLSCompliantAttribute?displayProperty=fullName> ，其會將它宣告為符合 CLS 標準。

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>另請參閱

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)