---
title: CA1008：列舉應該有零值 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548339"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008:列舉值中應該要有值為零的成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|類別|Microsoft. Design|
|中斷變更|不中斷-當系統提示您將**None**值新增至非旗標列舉時。中斷-當系統提示您重新命名或移除任何列舉值時。|

## <a name="cause"></a>原因
 未套用的列舉不 <xref:System.FlagsAttribute?displayProperty=fullName> 會定義值為零的成員，或已套用的列舉會 <xref:System.FlagsAttribute> 定義值為零的成員，但其名稱不是 ' None '，或列舉會定義多個零值的成員。

## <a name="rule-description"></a>規則描述
 未初始化列舉的預設值與其他實數值型別一樣，是零。 非旗標−屬性化列舉應定義值為零的成員，讓預設值是列舉的有效值。 如有需要，請將成員命名為 ' None '。 否則，請將零指派給最常使用的成員。 請注意，根據預設，如果宣告中未設定第一個列舉成員的值，其值為零。

 如果已套用的列舉 <xref:System.FlagsAttribute> 定義了零值成員，其名稱應該是 ' None '，表示列舉中未設定任何值。 針對任何其他目的使用零值成員，會與使用相同 <xref:System.FlagsAttribute> ，因為和和或位運算子對成員毫無用處。 這表示應該只將值零指派給一個成員。 請注意，如果有多個值為零的成員出現在旗標屬性列舉中， `Enum.ToString()` 則會針對非零的成員傳回不正確的結果。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正非旗標−屬性化列舉的此規則違規，請定義值為零的成員。這是不中斷的變更。 針對定義零值成員的旗標屬性列舉，請將此成員命名為 ' None '，並刪除值為零的其他任何成員。這是一種重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除了先前隨附的旗標屬性列舉以外，請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個符合規則的列舉，以及 `BadTraceOptions` 違反規則的列舉。

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700:不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712:不要使用類型名稱作為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Enum?displayProperty=fullName>
