---
title: "CA1707： 識別項不應包含底線 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 437085b76e1f9595c6db70fce798942df85a0292
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707：識別項不應包含底線
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|分類|Microsoft.Naming|  
|中斷變更|中斷-產生的組件時<br /><br /> 非中斷-產生型別參數時|  
  
## <a name="cause"></a>原因  
 識別項名稱包含底線 (_) 字元。  
  
## <a name="rule-description"></a>規則描述  
 根據慣例，識別項名稱不包含底線 (_) 字元。 此規則會檢查命名空間、 類型、 成員和參數。  
  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 從名稱中移除所有的底線字元。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)