---
title: CA1809： 避免使用過多區域變數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63bdcf0ea8363e6deb16034011d0a4446594171f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809：避免使用過多區域變數
|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 成員包含 64 個以上的區域變數，其中有些可能是編譯器產生。  
  
## <a name="rule-description"></a>規則描述  
 常見的效能最佳化會將值儲存在處理器暫存器而不是在記憶體中，這指*註冊 （enregistering)*值。 Common language runtime 會視為最多 64 個區域變數 enregistration。 不是機率的變數放在堆疊上，而且必須移至前操作的暫存器。 若要允許機會所有區域變數都能註冊、 本機變數設為 64 的數目限制。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請重構要使用不超過 64 個區域變數的實作。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果效能不是問題，就會隱藏此規則的警告，或停用規則，安全。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)