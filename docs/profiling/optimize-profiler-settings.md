---
title: 優化 Profiler 設定 |Microsoft Docs
description: 瞭解 Visual Studio 中的 [效能分析工具] 和 [診斷工具] 視窗有許多不同的設定，這些設定會影響工具的整體效能。
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 482ee640f4b84348e00f2f3da42a4dbe13f73460
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722837"
---
# <a name="optimizing-profiler-settings"></a>優化 Profiler 設定

Visual Studio 中的 [效能分析工具] 和 [診斷工具] 視窗有許多不同的設定，這些設定會影響工具的整體效能。 變更某些設定可能會導致分析快速執行，或在處理工具的結果時造成額外的等候時間。 以下是特定設定的摘要及其對效能的影響。

## <a name="symbol-settings"></a>符號設定

偵錯工具選項中所找到的符號設定 (**Debug > 選項 > 符號** 或 **工具 > 選項 > 錯 > 符號** ，) 在工具中產生結果所需的時間會有很大的影響。 啟用符號伺服器或使用 **_NT_SYMBOL_PATH** ，會讓分析工具為報表中的每個載入的模組要求符號。 目前，分析工具一律會自動載入所有符號，不論自動符號載入喜好設定為何。

![符號載入頁面](../profiling/media/symbolloading.png "符號載入")

您可以在 [ **輸出** ] 視窗中的 [ **診斷工具** ] 標題底下看到符號載入的進度。

![符號載入進度](../profiling/media/symbolloadingprogress.png "符號載入進度")

下載之後，會快取符號，以加速未來的分析，但仍需要載入和分析檔案。 如果符號載入減緩分析，請嘗試關閉符號伺服器，並清除符號快取。 相反地，會依賴針對您的專案在本機內建的符號。

## <a name="show-external-code"></a>顯示外部程式碼

**效能分析工具** 和 **診斷工具** 視窗內的許多工具都有使用者程式碼與外部程式碼的概念。 使用者程式碼是由開啟的解決方案或開啟工作區所建立的任何程式碼。 外部程式碼是其他任何東西。 藉由保持停用 [ **顯示外部程式碼** ] 設定，或 **只顯示 [我** 的程式碼] 已啟用，您就可以讓工具將外部程式碼匯總成單一的第一個層級框架，大幅減少顯示結果所需的處理量。 這可讓使用者查看在外部程式碼中所呼叫的程式碼，該程式碼會建立速度變慢的程式碼，同時維持資料的最小處理。 可能的話，請保持停用 [ **顯示外部程式碼** ]，並確定您已針對正在分析的 diagsession 開啟解決方案或工作區。

## <a name="trace-duration"></a>追蹤持續時間

分析較小的持續時間會導致較少的資料，更快進行分析。 一般來說，我們建議您嘗試將追蹤限制為不超過五分鐘的效能資料。 某些工具（例如 [ [CPU 使用量](../profiling/cpu-usage.md) ] 工具）可讓您在工具執行時暫停資料收集，讓您可以限制收集到您想要分析之案例的資料量。

## <a name="sampling-frequency"></a>取樣頻率

某些工具（例如 [ [CPU 使用量](../profiling/cpu-usage.md) ] 工具和 [ [NET Object 配置](../profiling/dotnet-alloc-tool.md) ] 工具）可讓您調整取樣頻率。 提高此取樣頻率可讓您更精確地測量，但會增加所產生的資料量。 一般來說，除非調查特定問題，否則最好將此設定保留為預設費率。

![診斷中樞屬性頁面](../profiling/media/diaghubpropertiespage.png "診斷中樞屬性頁面")

## <a name="see-also"></a>另請參閱

- [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [同時使用多個分析工具](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [了解效能收集方法](../profiling/understanding-performance-collection-methods-perf-profiler.md)
