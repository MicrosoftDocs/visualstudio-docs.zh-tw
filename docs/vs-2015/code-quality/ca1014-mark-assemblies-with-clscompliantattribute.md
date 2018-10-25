---
title: CA1014： 以標記組件 CLSCompliantAttribute |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 60bc7b47e2bfa275f1a1b4f28138e968f15bbfd9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859480"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014：以 CLSCompliantAttribute 標記組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [語言獨立性以及與語言無關的元件](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



