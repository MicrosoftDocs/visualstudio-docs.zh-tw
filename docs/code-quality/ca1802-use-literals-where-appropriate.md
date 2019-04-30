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
ms.openlocfilehash: f4dbafb4c6f7ad590244842ac3def0e26f8a14fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797063"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802:建議在適當時使用常值

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因

欄位宣告`static`並`readonly`(`Shared`和`ReadOnly`Visual Basic 中)，並在編譯時期會計算值進行初始化。

根據預設，此規則只會查看外部可見的欄位，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

值`static readonly`的宣告類型的靜態建構函式呼叫時，將會計算在執行階段的欄位。 如果`static readonly`欄位會初始化其宣告和靜態建構函式未明確宣告，編譯器會發出的靜態建構函式，將欄位初始化時。

值`const`欄位會在編譯時期計算並儲存在中繼資料，這樣會增加執行階段效能，它是相較於`static readonly`欄位。

因為在編譯時期計算指派給目標欄位的值，將宣告變更為`const`欄位，使在編譯時期而不是在執行階段計算的值。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，取代`static`並`readonly`修飾詞搭配`const`修飾詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

很安全隱藏這項規則的警告，或停用規則，如果效能不是問題。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1802.api_surface = private, internal
```

此類別 （效能） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示的型別`UseReadOnly`，會違反此規則，並為型別， `UseConstant`，符合規則。

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]