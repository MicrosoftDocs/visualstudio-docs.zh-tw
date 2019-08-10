---
title: CA2241:必須提供格式化方法的正確引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bdb8ef315c9702cc10352368aba7202a8f29f7f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920009"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241:必須提供格式化方法的正確引數

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
傳遞`format`至方法<xref:System.Console.WriteLine%2A>的字串引數 (例如、 <xref:System.Console.Write%2A>或<xref:System.String.Format%2A?displayProperty=fullName> ) 不包含對應至每個物件引數的格式專案, 反之亦然。

## <a name="rule-description"></a>規則描述
方法的引數 (例如<xref:System.Console.WriteLine%2A>、 <xref:System.Console.Write%2A>和<xref:System.String.Format%2A> ) 包含後面接著數個<xref:System.Object?displayProperty=fullName>實例的格式字串。 格式字串所組成的文字和內嵌的格式項目表單的 {索引 [，對齊] [: formatString]}。 'index' 是以零起始的整數，會指出需要格式化的物件。 如果物件在格式字串中沒有對應的索引, 則會忽略物件。 如果 ' index ' 所指定的物件不存在, <xref:System.FormatException?displayProperty=fullName>則會在執行時間擲回。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請提供每個物件引數的格式專案, 並提供每個格式專案的物件引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示兩個規則違規。

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]