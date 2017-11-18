---
title: "CA1701： 資源字串複合字應該使用的大小寫正確 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dee5b21724944ea26e89c2cd1ace556f1377848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701：資源字串複合字應該使用正確的大小寫
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|分類|Microsoft.Naming|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 資源字串包含不正確的大小寫的複合字。  
  
## <a name="rule-description"></a>規則描述  
 每個單字的資源字串分割成語彙基元，根據其大小寫。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。 造成違規的複合字的範例是"CheckSum"和"MultiPart"，這應該大小寫慣例為"Checksum"和"Multipart"，分別。 因為前一個常見的用法，幾個例外狀況內建規則，並且標示數個單字，例如 「 工具列 」 和 「 檔案名稱 」，應該為兩個不同的字大小寫慣例。 在此範例中，就會標示 「 工具列 」 和 「 檔案名稱 」。  
  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 文字變更為正確的大小寫。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果拼字檢查字典所辨識的複合字的兩個部分，且其目的是要使用兩個字。  
  
 您也可以加入至拼字檢查程式的自訂字典的複合字。 自訂字典中的文字不會造成違規。 如需詳細資訊，請參閱[How to： 自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1702：複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>另請參閱  
 [大小寫慣例](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [命名方針](/dotnet/standard/design-guidelines/naming-guidelines)