---
title: "Ca1820： 應該測試空白字串時，使用字串長度 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bfacf70dd1d23d0596815ad2f9fa3f51986aaad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820：應該使用字串長度測試空白字串
|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 使用字串比較為空字串<xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
## <a name="rule-description"></a>規則描述  
 比較字串，以<xref:System.String.Length%2A?displayProperty=fullName>屬性或<xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>方法的速度明顯比使用<xref:System.Object.Equals%2A>。 這是因為<xref:System.Object.Equals%2A>執行相當多的 MSIL 指示比<xref:System.String.IsNullOrEmpty%2A>或執行擷取的指令數目<xref:System.String.Length%2A>屬性值，並比較為零。  
  
 您應該注意，<xref:System.Object.Equals%2A>和<xref:System.String.Length%2A>= = 0 的行為不同的 null 字串。 如果您嘗試取得的值<xref:System.String.Length%2A>null 字串上的屬性，common language runtime 會擲回<xref:System.NullReferenceException?displayProperty=fullName>。 如果您執行的比較 null 字串與空字串，common language runtime 不會擲回例外狀況。比較會傳回`false`。 測試 null 並不會大幅影響這兩種方法的相對效能。 為目標時[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，使用<xref:System.String.IsNullOrEmpty%2A>方法。 否則，請使用<xref:System.String.Length%2A>= = 盡可能的比較。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更要使用的比較<xref:System.String.Length%2A>屬性以及測試 null 字串。 如果目標[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，使用<xref:System.String.IsNullOrEmpty%2A>方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果效能不是問題。  
  
## <a name="example"></a>範例  
 下列範例說明不同的技術，可用來尋找空白的字串。  
  
 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]