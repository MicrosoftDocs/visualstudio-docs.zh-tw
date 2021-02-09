---
title: 測量 Python 程式碼的效能
description: 在使用 CPython 型解譯器時，以 Visual Studio 分析工具來檢查 Python 程式碼的效能。
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d860acad409f553a90186e6898077e7bfd81dd90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918875"
---
# <a name="profile-python-code"></a>分析 Python 程式碼

您可在使用 CPython 型解譯器時分析 Python 應用程式。 (請參閱[功能矩陣：分析](overview-of-python-tools-for-visual-studio.md#matrix-profiling)以了解這項功能在不同版本 Visual Studio 中的可用性。)

## <a name="profiling-for-cpython-based-interpreters"></a>CPython 型解譯器的分析

程式碼剖析是透過 [ **Debug**  >  **啟動 Python 分析]** 功能表命令來啟動，它會開啟設定對話方塊：

![分析設定對話方塊](media/profiling-start.png)

當您選取 [確定] 時，分析工具會執行並開啟效能報告，您可以透過該報告探索應用程式中的執行時間：

![分析效能報告](media/profiling-results.png)

> [!Note]
> 當您對 Python 應用程式進行分析時 Visual Studio 會在進程的存留期間收集資料。 目前無法暫停分析。 我們想要聽聽您對於未來功能的意見反應。 請使用此頁面底部的 [產品意見反應] 按鈕。

## <a name="profiling-for-ironpython"></a>針對 IronPython 的分析

因為 IronPython 不是 CPython 型解譯器，所以上述分析功能無法運作。

請改為直接將 *ipy.exe* 作為目標應用程式啟動來使用 Visual Studio .NET 分析工具，並使用適當的引數來啟動您的啟動指令碼。 將 `-X:Debug` 包含在命令列中，以確保可偵錯與分析您的所有 Python 程式碼。 此引數會產生包含在 IronPython 執行階段及您程式碼上所花費時間的效能報告。 您的程式碼是以損害名稱來識別。

此外，IronPython 本身也有一些內建的分析功能，但它目前並沒有良好的視覺化檢視。 請參閱 [IronPython 分析工具 (英文)](/archive/blogs/curth/an-ironpython-profiler) (MSDN 部落格) 來查看可用內容。