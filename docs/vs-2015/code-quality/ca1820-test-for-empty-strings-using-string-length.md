---
title: Ca1820： 應該測試空白字串時，使用字串長度 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ec8a786936208a4839645f854d587bc6cb2b5448
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221563"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820：應該使用字串長度測試空白字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因
 使用字串比較為空字串<xref:System.Object.Equals%2A?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 比較字串使用<xref:System.String.Length%2A?displayProperty=fullName>屬性或<xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>方法的速度明顯比使用<xref:System.Object.Equals%2A>。 這是因為<xref:System.Object.Equals%2A>執行更多的 MSIL 指示，兩個<xref:System.String.IsNullOrEmpty%2A>或執行擷取的指令數目<xref:System.String.Length%2A>屬性值，並比較它與零。

 您應該注意可<xref:System.Object.Equals%2A>和<xref:System.String.Length%2A>= = 0 的行為不同的 null 字串。 如果您嘗試取得的值<xref:System.String.Length%2A>屬性為 null 的字串，common language runtime 會擲回<xref:System.NullReferenceException?displayProperty=fullName>。 如果您執行 null 字串與空字串之間的比較，common language runtime 不會擲回例外狀況;比較會傳回`false`。 測試 null，不會大幅影響這兩種方法的相對效能。 為目標時[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]，使用<xref:System.String.IsNullOrEmpty%2A>方法。 否則，請使用<xref:System.String.Length%2A>= = 盡可能的比較。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更要使用的比較<xref:System.String.Length%2A>屬性以及測試，null 字串。 如果目標[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]，使用<xref:System.String.IsNullOrEmpty%2A>方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全地隱藏此規則的警告，如果效能不成問題。

## <a name="example"></a>範例
 下列範例說明用來尋找空字串的不同技術。

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]



