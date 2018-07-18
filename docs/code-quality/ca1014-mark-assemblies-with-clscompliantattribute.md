---
title: CA1014：以 CLSCompliantAttribute 標記組件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51e5a43a402bb215a939b37354dd30f24e4d5d14
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898176"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014：以 CLSCompliantAttribute 標記組件
|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 組件沒有<xref:System.CLSCompliantAttribute?displayProperty=fullName>套用至它的屬性。

## <a name="rule-description"></a>規則描述
 Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會要求所有組件明確表示 cls 符合性與<xref:System.CLSCompliantAttribute>。 如果屬性不存在組件上，不符合標準的組件。

 很可能是符合 CLS 標準的組件包含型別或型別不相容的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入組件中的屬性。 而不是標示為不相容的整個組件，您應該判斷何種類型或類型成員不相容，並將標示這些項目，在這種情況。 可能的話，請您應該為不合格的成員提供符合 CLS 標準的替代方式，以便廣泛的可能使用者可以存取您的組件的所有功能。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 如果您不想要符合標準的組件，將屬性套用並設定其值為`false`。

## <a name="example"></a>範例
 下列範例示範具有的組件<xref:System.CLSCompliantAttribute?displayProperty=fullName>套用的屬性宣告符合 CLS 標準。

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>另請參閱
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)