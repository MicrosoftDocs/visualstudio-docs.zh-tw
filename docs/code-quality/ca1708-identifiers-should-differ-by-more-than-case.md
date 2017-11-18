---
title: "CA1708： 識別項不應該不同不僅為大小寫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda7936a1a701b1b51957a7038db496f70ddd9c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708：識別項名稱不應該只靠大小寫區別
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 當轉換成小寫，兩種類型、 成員、 參數或完整限定的命名空間的名稱完全相同。  
  
## <a name="rule-description"></a>規則描述  
 因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 例如，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]是廣泛使用不區分大小寫的語言。  
  
 此規則會引發公開可見的成員。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 選取時，它會以不區分大小寫的方式與其他識別項是唯一的名稱。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 程式庫可能無法使用的所有可用語言[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。  
  
## <a name="example-of-a-violation"></a>發生違規的範例  
 下列範例會示範這項規則的違規情形。  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)