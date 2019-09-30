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
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233422"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820:應該使用字串長度測試空白字串

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|分類|Microsoft.Performance|
|重大變更|不中斷|

## <a name="cause"></a>原因

使用<xref:System.Object.Equals%2A?displayProperty=nameWithType>，將字串與空字串進行比較。

## <a name="rule-description"></a>規則描述

使用<xref:System.String.Length%2A?displayProperty=nameWithType>屬性<xref:System.Object.Equals%2A>或方法比較字串，會比使用更快。 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 這是因為<xref:System.Object.Equals%2A>執行的<xref:System.String.Length%2A> MSIL 指令會<xref:System.String.IsNullOrEmpty%2A>比或執行來抓取屬性值並將它與零進行比較的指令數目明顯更多。

對於 null 字串， <xref:System.Object.Equals%2A>和`<string>.Length == 0`的行為不同。 如果您嘗試在 null 字串上取得<xref:System.String.Length%2A>屬性的值，則 common language runtime <xref:System.NullReferenceException?displayProperty=fullName>會擲回。 如果您在 null 字串和空字串之間執行比較，common language runtime 不會擲回例外狀況並`false`傳回。 測試 null 並不會大幅影響這兩種方法的相對效能。 以 .NET Framework 2.0 或更新版本為<xref:System.String.IsNullOrEmpty%2A>目標時，請使用方法。 否則，請盡可能<xref:System.String.Length%2A>使用 = = 0 比較。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將比較變更為<xref:System.String.IsNullOrEmpty%2A> [使用方法]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果效能不是問題，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例

下列範例說明用來尋找空字串的不同技術。

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]