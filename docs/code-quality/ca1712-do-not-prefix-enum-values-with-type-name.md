---
title: CA1712：不要使用類型名稱做為列舉值的前置字元
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b6d8a5ebba4f746c7418fcfb28a61d98949441e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712：不要使用類型名稱做為列舉值的前置字元
|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 列舉包含的成員名稱開頭的列舉型別名稱。

## <a name="rule-description"></a>規則描述
 列舉成員的名稱與型別名稱沒有前置字元，因為預期型別資訊會由開發工具提供。

 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要學習新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的時間。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請從列舉成員中移除型別名稱前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示後面接著已更正版本命名錯誤列舉型別。

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1711：識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Enum?displayProperty=fullName>