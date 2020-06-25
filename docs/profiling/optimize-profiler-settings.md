---
title: 優化 Profiler 設定 |Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9ff76364026230d08d03c91d14bddba3c325e7be
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290188"
---
# <a name="optimizing-profiler-settings"></a>優化 Profiler 設定

Visual Studio 中的 [效能分析工具] 和 [診斷工具] 視窗有許多不同的設定，會影響工具的整體效能。 變更某些設定可能會導致分析快速執行，或在處理工具中的結果時造成額外的等候時間。 以下摘要說明特定設定及其對效能的影響。

## <a name="symbol-settings"></a>符號設定

偵錯工具選項（**Debug > 選項 > 符號**）中找到的符號設定，會明顯影響在工具中產生結果所需的時間。 啟用符號伺服器或使用 **_NT_SYMBOL_PATH** ，會導致分析工具要求報表中每個已載入模組的符號。 目前，分析工具一律會自動載入所有符號，而不論自動符號載入喜好設定為何。

![[符號載入] 頁面](../profiling/media/symbolloading.png "符號載入")

在 [**輸出**] 視窗的 [**診斷工具**] 標題下，可以看到符號載入的進度。

![符號載入進度](../profiling/media/symbolloadingprogress.png "符號載入進度")

一旦下載，就會快取符號，這會加速未來的分析，但仍需要載入和分析檔案。 如果符號載入會降低分析速度，請嘗試關閉符號伺服器並清除符號快取。 相反地，請依賴在本機為您的專案建立的符號。

## <a name="show-external-code"></a>顯示外部程式碼

[**效能**分析工具] 和 [**診斷工具**] 視窗內的許多工具都有使用者程式碼與外部程式碼的概念。 使用者程式碼是由開啟的方案或開啟的工作區所建立的任何程式碼。 外部程式碼則是其他任何專案。 藉由保持 [**顯示外部程式碼**] 設定為 [已停用] 或 [**只顯示我**的程式碼已啟用]，您就可以讓工具將外部程式碼匯總到單一的第一個層級框架，大幅減少顯示結果所需的處理量。 如此一來，使用者就可以查看在外部程式碼中，建立緩慢的呼叫，同時將資料保持在最小的狀態。 可能的話，請保持停用 [**顯示外部程式碼**]，並確定您已針對正在分析的 diagsession 開啟解決方案或工作區。

## <a name="trace-duration"></a>追蹤持續時間

分析較小的持續時間會產生較少的資料，這會更快速地進行分析。 一般來說，我們建議您嘗試將追蹤限制為不超過五分鐘的效能資料。 某些工具（例如[CPU 使用量](../profiling/cpu-usage.md)工具）可讓您在工具執行時暫停資料收集，讓您可以限制收集到您想要分析之案例的資料量。

## <a name="sampling-frequency"></a>取樣頻率

某些工具（例如 [ [CPU 使用量](../profiling/cpu-usage.md)] 工具和 [[網路物件配置](../profiling/dotnet-alloc-tool.md)] 工具）可讓您調整取樣頻率。 增加此取樣頻率可讓您更精確地測量，但會增加所產生的資料量。 一般來說，除非調查特定問題，否則最好不要以預設速率保留此設定。

![診斷中樞屬性頁面](../profiling/media/diaghubpropertiespage.png "診斷中樞屬性頁面")

## <a name="see-also"></a>另請參閱

- [使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [同時使用多個 profiler 工具](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [了解效能收集方法](../profiling/understanding-performance-collection-methods-perf-profiler.md)
