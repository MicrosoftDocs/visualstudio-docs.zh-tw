---
title: 行動性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf1d9402294980a2202bbd3ab99c03b5e438eaa
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448868"
---
# <a name="mobility-warnings"></a>行動性警告
行動性警告支援有效率的電源使用方式。

## <a name="in-this-section"></a>本章節內容

|規則|描述|
|----------|-----------------|
|[CA1600：不要使用 Idle 處理序優先權](../code-quality/ca1600-do-not-use-idle-process-priority.md)|請勿將處理序優先權設定為 Idle。 具有 System.Diagnostics.ProcessPriorityClass.Idle 的處理序會在應該閒置的時候佔用 CPU，因而阻礙 CPU 待命。|
|[CA1601：不要使用會妨礙電源狀態變更的計時器](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。|
