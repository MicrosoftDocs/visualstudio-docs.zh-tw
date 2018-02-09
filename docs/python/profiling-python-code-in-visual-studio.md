---
title: "在 Visual Studio 中測量 Python 程式碼的效能 | Microsoft Docs"
description: "如何在使用 CPython 型解譯器時，以 Visual Studio 分析工具來檢查 Python 程式碼的效能。"
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 7f9fb355d35a5c2dcebff6fc1c94c52234e672a0
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="profiling-python-code"></a>分析 Python 程式碼

Visual Studio 支援在使用 CPython 型解譯器時分析 Python 應用程式。

若要進行分析，請執行 [分析] > [啟動 Python 分析] 功能表命令，這將會開啟設定對話方塊：

![分析設定對話方塊](media/profiling-start.png)

當您選取 [確定] 時，分析工具會執行並開啟效能報告，您可以透過該報告探索應用程式中的執行時間：

![分析效能報告](media/profiling-results.png)

如需示範，請參閱[分析 Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567) 影片 (Microsoft Virtual Academy，3 分 00 秒)。

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567]

## <a name="profiling-for-ironpython"></a>針對 IronPython 的分析

因為 IronPython 不是 CPython 型解譯器，所以上述分析功能無法運作。

請改為直接將 `ipy.exe` 作為目標應用程式啟動來使用 Visual Studio .NET 分析工具，並使用適當的引數來啟動您的啟動指令碼。 將 `-X:Debug` 包含在命令列中，以確保可偵錯與分析您的所有 Python 程式碼。 此引數會產生包含在 IronPython 執行階段及您程式碼上所花費時間的效能報告。 您的程式碼是以損害名稱來識別。

此外，IronPython 本身也有一些內建的分析功能，但它目前並沒有良好的視覺化檢視。 請參閱 [IronPython 分析工具 (英文)](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (MSDN 部落格) 來查看可用內容。