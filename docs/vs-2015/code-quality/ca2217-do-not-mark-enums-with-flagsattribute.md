---
title: CA2217：不要以 FlagsAttribute 標記列舉 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b584e355f5b64984f57dd17606dfb0a2f781c62d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547663"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217:不要以 FlagsAttribute 標記列舉
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的列舉會以標示 <xref:System.FlagsAttribute> ，而且有一或多個值不是兩個的冪，或在列舉上有其他已定義值的組合。

## <a name="rule-description"></a>規則描述
 <xref:System.FlagsAttribute>只有當列舉中所定義的每個值是二的乘冪，或已定義值的組合時，列舉才會出現。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請 <xref:System.FlagsAttribute> 從列舉中移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示列舉（Color），其中包含值3，這不是2的乘冪，也不是任何已定義值的組合。 色彩列舉不應標記為 <xref:System.FlagsAttribute> 。

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]

## <a name="example"></a>範例
 下列範例顯示的列舉天數，符合標記 FlagsAttribute 的需求。

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName>
