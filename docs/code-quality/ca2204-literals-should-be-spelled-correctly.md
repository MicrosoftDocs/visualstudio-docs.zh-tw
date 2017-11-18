---
title: "CA2204： 常值應該使用正確的拼字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fca8484b3231a92ab3a425c4661229236833642
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204：常值必須使用正確的拼字
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 方法會傳遞常值字串，用於參數或需要的當地語系化的字串和常值字串屬性包含一或多個 Microsoft 拼字檢查程式庫無法辨識的字。  
  
## <a name="rule-description"></a>規則描述  
 此規則會檢查常值字串做為值傳遞至參數或屬性，當一或多個下列情況為 true:  
  
-   <xref:System.ComponentModel.LocalizableAttribute>參數或屬性的屬性設定為 true。  
  
-   參數或屬性名稱包含 「 文字 」、 「 訊息 」，或 「 標題 」。  
  
-   傳遞至 Console.Write 或 Console.WriteLine 方法將字串參數的名稱是"value"format"。  
  
 此規則會將常值字串剖析成文字，複合字 token 化，並檢查每個字/語彙基元的拼字。 剖析演算法的相關資訊，請參閱[CA1704： 識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 根據預設，會使用拼字檢查程式的英文 (en) 版。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，更正單字的拼字，或將該字加入至自訂字典。 如需如何使用自訂字典，請參閱[How to： 自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 正確拼寫正確的單字會降低所需的新軟體程式庫的學習曲線。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703：資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)