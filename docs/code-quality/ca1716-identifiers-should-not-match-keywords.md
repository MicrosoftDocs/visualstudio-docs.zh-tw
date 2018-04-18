---
title: CA1716： 識別項不應該符合關鍵字 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c695f66a096614621cee2f38aed3e8fd6d970bed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716：識別項名稱不應該和關鍵字相符
|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 命名空間、 型別或 viritual 或介面成員的名稱符合程式語言中的保留的關鍵字。  
  
## <a name="rule-description"></a>規則描述  
 命名空間、 類型、 識別碼和虛擬和介面成員不應該符合 common language runtime 為目標的語言所定義的關鍵字。 根據所使用的語言和關鍵字，編譯器錯誤模稜兩可以對程式庫難以使用。  
  
 此規則會檢查對下列語言的關鍵字：  
  
-   Visual Basic  
  
-   C#  
  
-   C++/CLI  
  
 不區分大小寫用於[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]關鍵字，且區分大小寫比較用於其他語言。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 關鍵字的清單中選取名稱，不會出現。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果您相信識別項不會混淆的 API，使用者和程式庫是可用於所有可用的語言中，您可以隱藏此規則的警告[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。