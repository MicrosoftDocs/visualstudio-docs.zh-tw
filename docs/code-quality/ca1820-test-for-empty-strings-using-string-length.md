---
title: CA1820:應該使用字串長度測試空白字串
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb5160ef663375ee3dd4b45797e8f4536acdf793
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66744643"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820:應該使用字串長度測試空白字串

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因

使用字串比較為空字串<xref:System.Object.Equals%2A?displayProperty=nameWithType>。

## <a name="rule-description"></a>規則描述

比較字串使用<xref:System.String.Length%2A?displayProperty=nameWithType>屬性或<xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>方法的速度比使用<xref:System.Object.Equals%2A>。 這是因為<xref:System.Object.Equals%2A>執行更多的 MSIL 指示，兩個<xref:System.String.IsNullOrEmpty%2A>或執行擷取的指令數目<xref:System.String.Length%2A>屬性值，並比較它與零。

Null 的字串，請<xref:System.Object.Equals%2A>和`<string>.Length == 0`表現的行為。 如果您嘗試取得的值<xref:System.String.Length%2A>屬性為 null 的字串，common language runtime 會擲回<xref:System.NullReferenceException?displayProperty=fullName>。 如果您執行 null 字串與空字串之間的比較，通用語言執行平台並不會擲回例外狀況，並傳回`false`。 測試 null，不會大幅影響這兩種方法的相對效能。 當目標.NET Framework 2.0 或更新版本，使用<xref:System.String.IsNullOrEmpty%2A>方法。 否則，請使用<xref:System.String.Length%2A>= = 0 的比較，可能的話。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，變更要使用的比較<xref:System.String.IsNullOrEmpty%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它是安全地隱藏此規則的警告，如果效能不成問題。

## <a name="example"></a>範例

下列範例說明用來尋找空字串的不同技術。

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]