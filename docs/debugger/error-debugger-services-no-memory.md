---
title: 記憶體不足的服務偵錯工具 |Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854015"
---
# <a name="debugger-services-running-out-of-memory"></a>記憶體不足的服務偵錯工具
服務進行偵錯記憶體不足而造成偵錯工作階段終止。

## <a name="to-investigate-this-error-on-windows"></a>若要調查此錯誤在 Windows 上
- 您可以檢查處理序記憶體圖表中**診斷工具**視窗來查看記憶體中的大量成長時，是否要發生的目標應用程式。 如果是，使用**記憶體使用量**工具來診斷功能為基礎的問題，請參閱[分析記憶體使用量](../profiling/memory-usage.md)。

- 如果目標應用程式似乎不會耗用大量記憶體，使用**工作管理員**視窗來查看記憶體使用量的 Visual Studio (devenv.exe)，背景工作處理序 (msvsmon.exe)，或 VS Code (vsdbg.exe/vsdbg-ui.exe)判斷是否為偵錯工具的問題。 如果記憶體不足所執行的處理序 devenv.exe，請考慮減少執行的 Visual Studio 擴充功能的數目。

## <a name="see-also"></a>另請參閱
- [部落格文章：偵錯時分析 CPU 和記憶體](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [關於記憶體管理](/windows/win32/memory/about-memory-management)
