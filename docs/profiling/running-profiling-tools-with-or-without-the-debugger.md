---
title: 使用或不使用偵錯工具來執行分析工具 | Microsoft Docs
description: 瞭解可用於程式碼剖析工具的不同模式之間的差異
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bd8f90c586366a298ba96009dfe5d87a042141b
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970297"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>使用或不使用偵錯工具來執行分析工具

Visual Studio 提供各種效能測量和分析工具的選擇。 某些工具（例如 CPU 使用量和記憶體使用量）可以使用或不使用偵錯工具來執行，也可以在發行或偵錯工具設定上執行。 出現在 [ [診斷工具] 視窗](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) 中的工具只會在偵測會話期間執行。 出現在 [效能分析工具](../profiling/profiling-feature-tour.md#post_mortem) 中的工具會在沒有偵錯工具的情況下執行，而且您會在選擇停止和收集事後剖析後分析) 的資料 (之後分析結果。

>[!NOTE]
>您可以在 Windows 7 和更新版本中使用非偵錯工具的效能工具。 若要執行偵錯工具整合的分析工具，需要 Windows 8 或更新版本。

非偵錯工具的 [效能分析工具] 和偵錯工具整合的 [診斷工具] 提供不同資訊與體驗。 偵錯工具整合的工具會顯示變數值，並讓您使用中斷點。 非偵錯工具之工具可為您提供更接近終端使用者體驗的結果。

若要協助決定要使用的工具和結果，請考慮下列事項：

- 偵錯工具整合工具與非偵錯工具工具的比較
  - 外部效能問題 (例如檔案 I/O 或網路回應性問題) 在偵錯工具或非偵錯工具的工具中看起來沒有太大差異。
  - 偵錯工具本身會變更效能時間，因為它會執行必要的偵錯工具作業（例如攔截例外狀況和模組載入事件）。
  - 效能分析工具中的發行組建效能數位最精確且正確。 偵錯工具整合的工具結果最適合用來與其他與偵錯工具相關的度量比較，或是使用偵錯工具功能。
  - 某些工具（例如 .NET 物件組態工具）僅適用于非偵錯工具案例。
- Debug 與發行組建
  - 針對需要大量 CPU 的呼叫所造成的問題，發行與 debug 組建之間可能會有相當大的效能差異。 查看發行組建中是否有問題。
  - 如果只有在 debug 組建期間發生此問題，您可能不需要執行非偵錯工具工具。 針對發行組建問題，請決定偵錯工具整合工具所提供的功能是否有助於找出問題。
  - [發行] 組建提供最佳化功能，例如內嵌函式呼叫和常數、清除未用的程式碼路徑，以及無法採用偵錯工具所使用的方式來儲存變數。 Debug 組建中的效能數位較不精確，因為 debug 組建缺少這些優化。

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>偵錯時收集程式碼剖析資料

當您選取 [ **Debug**  >  **開始調試** 程式] 或按下 **F5** 來開始 Visual Studio 中的偵錯工具時，預設會顯示 [**診斷工具**] 視窗。 若要手動開啟，請選取 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。 [診斷工具] 視窗會顯示事件、處理序記憶體和 CPU 使用量的相關資訊。

![診斷工具視窗的螢幕擷取畫面](../profiling/media/diagnostictoolswindow.png "[診斷工具] 視窗")

- 使用工具列上的 **設定** 圖示來選擇是否要檢視 [記憶體使用量]、[UI 分析]，以及 [CPU 使用量]。

- 在 [**設定**] 下拉式清單中選取 [**設定**]，以開啟具有更多選項的 **診斷工具屬性頁面**。

- 如果您正在執行 Visual Studio Enterprise，可以前往 [**工具**  >  **選項**  >  **IntelliTrace**] 來啟用或停用 IntelliTrace。

在您停止偵錯時，診斷工作階段就會結束。

如需詳細資訊，請參閱

- [透過分析 CPU 使用量測量應用程式效能](../profiling/beginners-guide-to-performance-profiling.md)
- [在 Visual Studio 中測量記憶體使用量](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>[事件] 索引標籤

在偵錯工作階段期間，[診斷工具] 視窗的 [事件] 索引標籤會列出所發生診斷事件。 類別首碼 *中斷點*、檔案和其他專案，可讓您快速掃描 *清單中的* 類別，或略過不在意的類別。

您可以使用 [ **篩選** ] 下拉式清單，藉由選取或清除特定的事件類別，來篩選出和移出事件。

![診斷事件篩選的螢幕擷取畫面](../profiling/media/diagnosticeventfilter.png "診斷事件篩選器")

請使用搜尋方塊來尋找事件清單中的特定字串。 以下是搜尋符合四個事件之字串 *名稱* 的結果：

![診斷事件搜尋的螢幕擷取畫面](../profiling/media/diagnosticseventsearch.png "診斷事件搜尋")

如需詳細資訊，請參閱 [搜尋和篩選診斷工具視窗的事件索引標籤](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)。

## <a name="collect-profiling-data-without-debugging"></a>收集程式碼剖析資料但不偵錯

若要收集效能資料而不進行偵錯，您可以執行 [效能分析工具]。

1. 在 Visual Studio 中開啟專案時，將解決方案設定設為 [ **發行**]，然後選取 [ **本機 Windows 偵錯工具** ] (或 [ **本機電腦** ]) 作為部署目標。

1. 選取 [ **Debug**  >  **效能分析工具**]，或按 **Alt** + **F2**。

1. 在 [診斷工具] 的 [啟動] 頁面上，選取一或多個要執行的工具。 只有適用于專案類型、作業系統和程式設計語言的工具才會顯示。 選取 [顯示所有工具] 來另外查看針對這個診斷工作階段停用的工具。

   ![診斷工具的螢幕擷取畫面](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. 若要開始診斷工作階段，請選取 [開始]。

   當會話正在執行時，某些工具會在 [診斷工具] 頁面上顯示即時資料的圖表，以及用來暫停和繼續收集資料的控制項。

    ![效能分析工具的資料收集螢幕擷取畫面](../profiling/media/diaghubcollectdata.png "中樞收集資料")

1. 若要結束診斷工作階段，請選取 [停止收集]。

   分析的資料會出現在 **報表** 頁面上。

您可以儲存報表，並在 [診斷工具啟動] 頁面上的 [ **最近開啟的會話** ] 清單中開啟報表。

![診斷工具最近開啟的會話清單螢幕擷取畫面](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

如需詳細資訊，請參閱

- [分析 CPU 使用量](../profiling/cpu-usage.md)
- [分析 .NET 程式碼的記憶體使用量](../profiling/dotnet-alloc-tool.md)
- [分析記憶體使用量](../profiling/memory-usage-without-debugging2.md)
- [分析 .NET 非同步程式碼的效能](../profiling/analyze-async.md)
- [分析資料庫效能](../profiling/analyze-database.md)
- [分析 GPU 使用量](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>從命令列收集程式碼剖析資料

若要從命令列測量效能資料，您可以使用 Visual Studio 或遠端工具隨附的 VSDiagnostics.exe。 這有助於在未安裝 Visual Studio 的系統上捕獲效能追蹤，或針對效能追蹤的集合編寫腳本。 如需詳細指示，請參閱 [從命令列測量應用程式效能](../profiling/profile-apps-from-command-line.md)。