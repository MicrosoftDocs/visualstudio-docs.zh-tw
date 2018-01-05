---
title: "CA1703： 資源字串應該拼寫正確 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fd3073ca8191284e59559724411bb7e78a3c2fe9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703：資源字串應該拼寫正確
|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|分類|Microsoft.Naming|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。  
  
## <a name="rule-description"></a>規則描述  
 此規則的資源字串剖析成單字 (token 複合字)，並檢查每個字/語彙基元的拼字。 剖析演算法的相關資訊，請參閱[CA1704： 識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
 根據預設，會使用拼字檢查程式的英文 (en) 版。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請使用完整文字拼寫正確，或將單字加入到自訂字典。 如需如何使用自訂字典，請參閱[CA1704： 識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 正確拼寫正確的單字會減少學習新的軟體程式庫的時間。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)