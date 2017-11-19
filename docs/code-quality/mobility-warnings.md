---
title: "行動性警告 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fdcff36e689961200497298f3360fc0efb27f0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="mobility-warnings"></a>行動性警告
行動性警告支援有效率的用電量。  
  
## <a name="in-this-section"></a>本章節內容  
  
|規則|說明|  
|----------|-----------------|  
|[CA1600：不要使用 Idle 處理序優先權](../code-quality/ca1600-do-not-use-idle-process-priority.md)|請勿將處理序優先權設定為 Idle。 具有 System.Diagnostics.ProcessPriorityClass.Idle 的處理序會在應該閒置的時候佔用 CPU，因而阻礙 CPU 待命。|  
|[CA1601：不要使用會妨礙電源狀態變更的計時器](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。|