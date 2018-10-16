---
title: 行動性警告 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e73864234604f22ec15340740442505fec3e078
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270071"
---
# <a name="mobility-warnings"></a>行動性警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

行動性警告支援有效率的用電量。  
  
## <a name="in-this-section"></a>本節內容  
  
|規則|描述|  
|----------|-----------------|  
|[CA1600：不要使用 Idle 處理序優先權](../code-quality/ca1600-do-not-use-idle-process-priority.md)|請勿將處理序優先權設定為 Idle。 具有 System.Diagnostics.ProcessPriorityClass.Idle 的處理序會在應該閒置的時候佔用 CPU，因而阻礙 CPU 待命。|  
|[CA1601：不要使用會妨礙電源狀態變更的計時器](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。|



