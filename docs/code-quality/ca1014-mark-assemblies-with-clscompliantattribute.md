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
ms.openlocfilehash: 0ea7c0d4b9c1d8edea3c2d96f04114db47f3b0d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779504"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014:組件必須標記 CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 組件沒有<xref:System.CLSCompliantAttribute?displayProperty=fullName>套用屬性。

## <a name="rule-description"></a>規則描述
 Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會要求所有組件明確表示 cls 符合性與<xref:System.CLSCompliantAttribute>。 如果屬性不存在的組件，組件不符合規範。

 您有符合 CLS 標準的組件，以包含型別或型別不符合規範的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入組件中的屬性。 而不是標示為不符合規範的整個組件，您應該判斷何種類型或類型成員不符合規範，並將標示因此這些項目。 可能的話，您應該不符合規範的成員提供符合 CLS 標準的替代方案，如此廣泛的可能使用者可以存取您的組件的所有功能。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 如果您不想要符合規範的組件，將屬性套用，並將其值設定為`false`。

## <a name="example"></a>範例
 下列範例示範具有組件<xref:System.CLSCompliantAttribute?displayProperty=fullName>套用的屬性宣告符合 CLS 標準。

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>另請參閱

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)