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
ms.openlocfilehash: 323025eb03d2a949a970659aba2357c01ed8bfab
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921765"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712:不要使用類型名稱作為列舉值的前置字元

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
列舉包含成員, 其名稱開頭為列舉型別名稱。

## <a name="rule-description"></a>規則描述
列舉成員的名稱不會加上類型名稱的前置詞, 因為開發工具預期會提供類型資訊。

命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少學習新的軟體程式庫所需的時間, 並提高客戶對於開發 managed 程式碼專業知識的人員所開發之程式庫的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請從列舉成員中移除類型名稱前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示不正確命名的列舉, 後面接著更正的版本。

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1711識別碼不應有不正確的尾碼](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027 必須使用 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Enum?displayProperty=fullName>