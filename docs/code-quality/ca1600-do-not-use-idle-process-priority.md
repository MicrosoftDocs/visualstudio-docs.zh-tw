---
title: "CA1600： 不要使用 idle 處理序優先權 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e52a658bd6161542ce909b8294f33d6e4bf140ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600：不要使用 Idle 處理序優先權
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|分類|Microsoft.Mobility|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 此規則會發生於處理序會設定為`ProcessPriorityClass.Idle`。  
  
## <a name="rule-description"></a>規則描述  
 請勿將處理序優先權設定為 Idle。 處理程序`System.Diagnostics.ProcessPriorityClass.Idle`原本是閒置時，因而阻礙待命時，會佔用 CPU。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要設定處理程序`ProcessPriorityClass.BelowNormal`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 閒置處理序優先權，且可以安全地忽略行動考量時，才應該隱藏此規則。