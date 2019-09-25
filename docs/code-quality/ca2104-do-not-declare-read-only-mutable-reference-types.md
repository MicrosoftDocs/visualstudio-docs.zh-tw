---
title: CA2104:不要宣告唯讀的可變動參考型別
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232959"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104:不要宣告唯讀的可變動參考類型

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|分類|Microsoft.Security|
|重大變更|不中斷|

> [!NOTE]
> 規則 CA2104 已過時，將在未來的 Visual Studio 版本中移除。 它不會實作為[分析器](roslyn-analyzers-overview.md)，因為必須有複雜的分析，才能判斷類型的實際不可變性。

## <a name="cause"></a>原因

外部可見類型包含了可變動參考類型的外部可見唯讀欄位。

## <a name="rule-description"></a>規則描述

可變動類型是可以修改執行個體資料的類型。 <xref:System.Text.StringBuilder?displayProperty=fullName>類別是可變參考型別的範例。 它包含可以變更類別實例值的成員。 <xref:System.String?displayProperty=fullName>類別是不可變參考型別的範例。 在具現化之後，其值永遠不會變更。

參考型別字段（或中C++的C#指標）的唯讀修飾詞（[readonly](/dotnet/csharp/language-reference/keywords/readonly) in、Visual Basic 中的[readonly](/dotnet/visual-basic/language-reference/modifiers/readonly)和[const](/cpp/cpp/const-cpp) C++）可防止欄位被參考型別的其他實例所取代。 不過，修飾詞不會防止欄位的實例資料透過參考型別進行修改。

此規則可能會不慎顯示類型的違規，事實上就是不可變的。 在這種情況下，隱藏警告是安全的。

唯讀陣列欄位不受此規則的規範，而是會導致違反[CA2105：陣列欄位不應為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)規則。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請移除唯讀的修飾詞，如果可以接受中斷性變更，請將欄位取代為不可變的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果欄位類型是不可變的，則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示導致違反此規則的欄位宣告：

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]