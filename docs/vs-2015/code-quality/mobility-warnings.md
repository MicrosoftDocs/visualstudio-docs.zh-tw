---
title: 行動性警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9f5606540d55c0a2c4257ff397ad77cc55624b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655973"
---
# <a name="mobility-warnings"></a>行動性警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

行動性警告支援有效率的電源使用。

## <a name="in-this-section"></a>本節內容

|規則|說明|
|----------|-----------------|
|[CA1600:不要使用 Idle 處理序優先順序](../code-quality/ca1600-do-not-use-idle-process-priority.md)|請勿將處理序優先權設定為 Idle。 具有 System.Diagnostics.ProcessPriorityClass.Idle 的處理序會在應該閒置的時候佔用 CPU，因而阻礙 CPU 待命。|
|[CA1601:不要使用會妨礙電源狀態變更的計時器](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。|
