---
title: CA2104:不要宣告唯讀的可變動參考類型
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
ms.openlocfilehash: 40fdeefc2d664b80bb6e17c109349cb5912b0516
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077702"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104:不要宣告唯讀的可變動參考類型

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|分類|Microsoft.Security|
|中斷變更|非重大|

> [!NOTE]
> 規則 CA2104 已經過時，將 Visual Studio 的未來版本中移除。 它不會實作為[分析器](roslyn-analyzers-overview.md)因為複雜的分析所需來判斷實際的不變性型別。

## <a name="cause"></a>原因

外部可見類型包含了可變動參考類型的外部可見唯讀欄位。

## <a name="rule-description"></a>規則描述

可變動類型是可以修改執行個體資料的類型。 <xref:System.Text.StringBuilder?displayProperty=fullName>類別是可變動參考類型的範例。 它包含成員可以變更類別的執行個體的值。 不可變的參考類型的範例是<xref:System.String?displayProperty=fullName>類別。 已執行個體化之後，可以永遠不會變更其值。

唯讀修飾詞 ([readonly](/dotnet/csharp/language-reference/keywords/readonly)中C#， [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)在 Visual Basic 中，和[const](/cpp/cpp/const-cpp)在C++) 的參考類型欄位 (或指標中的C++)防止欄位的參考類型的不同執行個體取代。 不過，修飾詞不會防止執行個體資料的欄位正在修改透過參考類型。

此規則可能會不小心顯示類型的違規，事實上是，不可變。 在此情況下，它可安全地隱藏警告。

唯讀陣列欄位免套用此規則，但改為導致違反[CA2105:陣列欄位不應該為唯讀](../code-quality/ca2105-array-fields-should-not-be-read-only.md)規則。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，移除唯讀修飾詞，或是否可接受的重大變更，請使用不可變的類型取代欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它會安全地隱藏此規則的警告，如果欄位類型是不可變。

## <a name="example"></a>範例

下列範例顯示會導致違反此規則的欄位宣告：

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]