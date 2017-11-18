---
title: "CA1724： 類型名稱應該符合命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 556fd9eee1bc453d4f9782459050367e18a3193b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724：類型名稱不應該和命名空間相符
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 類型名稱符合[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]不區分大小寫的比較中的命名空間名稱。  
  
## <a name="rule-description"></a>規則描述  
 類型名稱不得符合 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 中定義的命名空間名稱。 違反此規則會降低程式庫的可用性。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 選取的名稱不符的類型名稱[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]類別程式庫命名空間。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 進行新開發，已知情況下會發生您必須在此隱藏此規則的警告。 隱藏警告之前，請審慎考慮如何文件庫的使用者可能會混淆所比對的名稱。 傳送文件庫，您可能要隱藏此規則的警告。