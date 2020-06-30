---
title: CA1820 應該：使用字串長度測試空字串 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545310"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820:應該使用字串長度測試空白字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|類別|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 使用，將字串與空字串進行比較 <xref:System.Object.Equals%2A?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 使用 <xref:System.String.Length%2A?displayProperty=fullName> 屬性或方法來比較字串 <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> ，會比使用的速度明顯更快 <xref:System.Object.Equals%2A> 。 這是因為 <xref:System.Object.Equals%2A> 執行的 MSIL 指令會比 <xref:System.String.IsNullOrEmpty%2A> 或執行來抓取 <xref:System.String.Length%2A> 屬性值並將它與零進行比較的指令數目明顯更多。

 您應該注意， <xref:System.Object.Equals%2A> 和 <xref:System.String.Length%2A> = = 0 的行為會因 null 字串而有所不同。 如果您嘗試在 <xref:System.String.Length%2A> null 字串上取得屬性的值，則 common language runtime 會擲回 <xref:System.NullReferenceException?displayProperty=fullName> 。 如果您在 null 字串和空字串之間執行比較，common language runtime 不會擲回例外狀況;比較會傳回 `false` 。 測試 null 並不會大幅影響這兩種方法的相對效能。 以為目標時 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] ，請使用 <xref:System.String.IsNullOrEmpty%2A> 方法。 否則，請盡可能使用 <xref:System.String.Length%2A> = = 比較。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將比較變更為使用 <xref:System.String.Length%2A> 屬性，並測試 null 字串。 如果目標 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 為，請使用 <xref:System.String.IsNullOrEmpty%2A> 方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果效能不是問題，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例說明用來尋找空字串的不同技術。

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
