---
title: 偵錯工具服務用盡記憶體 |Microsoft Docs
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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737846"
---
# <a name="debugger-services-running-out-of-memory"></a>記憶體不足的偵錯工具服務
調試服務已用盡記憶體，並導致調試進程終止。

## <a name="to-investigate-this-error-on-windows"></a>若要在 Windows 上調查此錯誤
- 您可以在 [**診斷工具**] 視窗中檢查進程記憶體圖表，以查看目標應用程式在記憶體中是否有大量的成長。 若是如此，請使用 [**記憶體使用量**] 工具來診斷基礎問題，請參閱[分析記憶體使用量](../profiling/memory-usage.md)。

- 如果目標應用程式似乎不會耗用大量的記憶體，請使用 [**工作管理員**] 視窗來查看 Visual Studio （devenv）、工作者進程（msvsmon）或 VS Code （vsdbg .exe/vsdbg-ui）的記憶體使用量，以判斷這是否為偵錯工具問題。 如果記憶體不足的進程是 devenv，請考慮減少執行的 Visual Studio 擴充功能數目。

## <a name="see-also"></a>請參閱
- [Blog 文章：在調試過程中分析 CPU 和記憶體](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [關於記憶體管理](/windows/win32/memory/about-memory-management)
