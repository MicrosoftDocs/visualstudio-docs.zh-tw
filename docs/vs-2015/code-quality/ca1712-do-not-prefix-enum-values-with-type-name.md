---
title: CA1712:不要使用型別名稱的列舉值的前置字元 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 19b64c0d7c45bb2425ca3e59bd56f5c251feef50
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189183"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712:不要使用類型名稱作為列舉值的前置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 列舉型別，包含其名稱開頭的列舉型別名稱的成員。

## <a name="rule-description"></a>規則描述
 因為類型資訊會預期由開發工具所提供的型別名稱不有前置列舉成員的名稱。

 命名慣例提供了通用程式庫 common language runtime 為目標。 這可減少需要學習新的軟體程式庫，並讓程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶深信的時間。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除列舉成員中的型別名稱前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示命名錯誤的列舉，後面接著已更正版本。

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1711:識別項不應該有不正確的後置詞](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Enum?displayProperty=fullName>
