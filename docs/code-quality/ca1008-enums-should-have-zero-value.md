---
title: CA1008：列舉值中應該要有值為零的成員
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f35fc55d9baa59481647ee82aee5ccdeb84e7196
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31902135"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008：列舉值中應該要有值為零的成員
|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|分類|Microsoft.Design|
|中斷變更|非中斷-當系統提示您新增**無**非旗標列舉的值。-系統會提示您重新命名或移除任何列舉值時中斷。|

## <a name="cause"></a>原因
 列舉型別沒有套用<xref:System.FlagsAttribute?displayProperty=fullName>沒有定義的值為零或已套用的列舉成員<xref:System.FlagsAttribute>成員會定義具有零值，但名稱不是 'None' 或列舉定義零值的多個成員。

## <a name="rule-description"></a>規則描述
 未初始化的列舉，如同其他實值類型的預設值為零。 非旗標屬性的列舉型別應該定義具有零值的預設值是有效的列舉值的成員。 如果可行，名稱的成員 'None'。 否則，將指派零到最常使用的成員。 請注意，根據預設，是否第一個列舉成員的值未在宣告中，設定其值為零。

 如果已列舉<xref:System.FlagsAttribute>套用定義零值成員，其名稱應該是 'None' 表示列舉中尚未設定任何值。 使用零值成員的任何其他目的使用 fci <xref:System.FlagsAttribute> ，AND 或位元運算子是毫無用處的成員。 這表示應該指派給該只能有一個成員值為零。 請注意，如果多個成員具有零值會在旗標屬性的列舉，`Enum.ToString()`的成員不是零，傳回不正確的結果。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正非旗標屬性的列舉，此規則的違規情形，定義其值為零，成員這是不中斷變更。 旗標屬性的列舉定義零值的成員，這個成員 'None' 的名稱，並刪除任何其他成員的值為零，這是一項重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏除了先前所提供的旗標屬性列舉型別，此規則的警告。

## <a name="example"></a>範例
 下列範例會示範符合規則的兩個列舉型別和列舉型別， `BadTraceOptions`，違反此規則。

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700：不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Enum?displayProperty=fullName>