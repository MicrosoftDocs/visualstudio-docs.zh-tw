---
title: 偵錯工具服務記憶體不足 |Microsoft Docs
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
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72737846"
---
# <a name="debugger-services-running-out-of-memory"></a>記憶體不足的偵錯工具服務
偵錯工具服務的記憶體用盡，導致偵錯工具終止。

## <a name="to-investigate-this-error-on-windows"></a>若要在 Windows 上調查此錯誤
- 您可以檢查 [ **診斷工具** ] 視窗中的 [處理常式記憶體] 圖形，查看目標應用程式是否遇到記憶體的大量成長。 如果是，請使用 [ **記憶體使用量** ] 工具來診斷什麼是基礎問題，請參閱 [分析記憶體使用量](../profiling/memory-usage.md)。

- 如果目標應用程式似乎沒有耗用海量儲存體，請使用 **工作管理員** 視窗來查看 Visual Studio ( # A0) 、背景工作進程 ( # A1) 或 VS Code ( # A2/vsdbg-ui.exe) 的記憶體使用量，以判斷這是否為偵錯工具的問題。 如果 devenv.exe 記憶體不足的進程，請考慮減少執行中 Visual Studio 擴充功能的數目。

## <a name="see-also"></a>另請參閱
- [Blog 文章：在進行調試時分析 CPU 與記憶體](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [關於記憶體管理](/windows/win32/memory/about-memory-management)
