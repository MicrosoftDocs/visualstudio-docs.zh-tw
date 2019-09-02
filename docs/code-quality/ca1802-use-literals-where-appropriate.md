---
title: CA1802:建議在適當時使用常值
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c6512f02d13c2eeb441f5b374c4785deffe22a22
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547061"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802:建議在適當時使用常值

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft.Performance|
|中斷變更|不中斷|

## <a name="cause"></a>原因

欄位已`static`宣告和`readonly` `Shared` (`ReadOnly`在 Visual Basic 中), 並使用在編譯時期可的值進行初始化。

根據預設, 此規則只會查看外部可見的欄位, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

呼叫宣告類型的`static readonly`靜態函式時, 會在執行時間計算欄位的值。 `static readonly`如果欄位在宣告時初始化, 而且未明確宣告靜態的函式, 則編譯器會發出靜態的函式來初始化欄位。

`const`欄位的值會在編譯時期計算並儲存在中繼資料中, 這會在與`static readonly`欄位比較時增加執行時間效能。

因為指派給目標欄位的值是在編譯時期可, 所以請將宣告變更為`const`欄位, 以便在編譯時期 (而不是在執行時間) 計算該值。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形, 請`static`以`readonly` `const`修飾詞取代和修飾詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以放心地隱藏此規則的警告, 或停用規則 (如果效能不成問題)。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (效能) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示的類型`UseReadOnly`違反規則, 以及符合規則的`UseConstant`類型。

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]