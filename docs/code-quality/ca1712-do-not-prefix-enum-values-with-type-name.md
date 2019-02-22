---
title: CA1712:不要使用類型名稱作為列舉值的前置字元
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd15e582f7654f82e343a0175ccf9ed18254d904
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921727"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712:不要使用類型名稱作為列舉值的前置字元

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

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1711:識別項不應該有不正確的後置詞](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Enum?displayProperty=fullName>