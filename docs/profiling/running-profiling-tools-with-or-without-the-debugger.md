---
title: 使用或不使用偵錯工具來執行分析工具 | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed4cf1cce3ba677b5232c86b7abb1386d4d1dc50
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597527"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>使用或不使用偵錯工具來執行分析工具

Visual Studio 提供各種效能測量和分析工具的選擇。 其中有些工具 (例如 [CPU 使用量] 和 [記憶體使用量]) 可以使用或不使用偵錯工具來執行，也可以在 [發行] 或 [偵錯] 組建組態上執行。 [應用程式時間軸] 之類的 [效能分析工具] 可以在 [偵錯] 或 [發行] 組建上執行。 偵錯工具整合的工具 (例如 [診斷工具] 視窗和 [事件] 索引標籤) 只會在偵錯工作階段期間執行。

>[!NOTE]
>您可以在 Windows 7 和更新版本中使用非偵錯工具的效能工具。 若要執行偵錯工具整合的分析工具，需要 Windows 8 或更新版本。

非偵錯工具的 [效能分析工具] 和偵錯工具整合的 [診斷工具] 提供不同資訊與體驗。 偵錯工具整合的工具會顯示中斷點和變數值。 非偵錯工具之工具可為您提供更接近終端使用者體驗的結果。

若要協助決定要使用哪些工具和結果，請考慮下列各點：

- 外部效能問題 (例如檔案 I/O 或網路回應性問題) 在偵錯工具或非偵錯工具的工具中看起來沒有太大差異。
- 對於 CPU 密集運算呼叫所造成的問題，在 [發行] 與[偵錯] 組建之間可能會有相當大的效能差異。 請檢查 [發行] 組建中是否存在問題。
- 如果只在 [偵錯] 組建期間發生此問題，您可能不需要執行非偵錯工具的工具。 若為 [發行] 組建問題，請決定偵錯工具是否會協助進行深入調查。
- [發行] 組建提供最佳化功能，例如內嵌函式呼叫和常數、清除未用的程式碼路徑，以及無法採用偵錯工具所使用的方式來儲存變數。 由於 [偵錯] 組建缺少這些最佳化功能，因此偵錯工具整合的工具中效能數字較不準確。
- 偵錯工具本身在執行必要的偵錯工具作業 (例如攔截例外狀況和模組載入事件) 時會變更效能時間。
- [效能分析工具] 中的 [發行] 組建效能數字最精確且準確。 偵錯工具整合的工具結果最適合與其他偵錯相關的度量進行比較。

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a>偵錯時收集程式碼剖析資料

當您在 Visual Studio 中選取 [偵錯] > [開始偵錯] 或按下 **F5** 來啟動偵錯時，預設會出現 [診斷工具] 視窗。 若要手動加以開啟，請選取 [偵錯] > [視窗] > [顯示診斷工具]。 [診斷工具] 視窗會顯示事件、處理序記憶體和 CPU 使用量的相關資訊。

![診斷工具](../profiling/media/diagnostictools-update1.png "診斷工具")

- 使用工具列上的**設定**圖示來選擇是否要檢視 [記憶體使用量]、[UI 分析]，以及 [CPU 使用量]。

- 選取 [設定] 下拉式清單中的 [設定]，以開啟具有更多選項的 [診斷工具屬性頁]。

- 若正在執行 Visual Studio Enterprise，您可以在 Visual Studio [工具] > [選項] > [IntelliTrace] 下啟用或停用 IntelliTrace。

在您停止偵錯時，診斷工作階段就會結束。

您也可以檢視用於遠端偵錯目標的 [診斷工具]。 如需遠端偵錯和分析，Visual Studio 遠端偵錯工具必須安裝在遠端目標並於其上執行。
- 如需遠端偵錯和分析傳統型應用程式專案，請參閱[遠端偵錯](../debugger/remote-debugging.md)。
- 如需遠端偵錯和分析 UWP 應用程式，請參閱[對遠端電腦上的 UWP 應用程式進行偵錯](../debugger/run-windows-store-apps-on-a-remote-machine.md)。

### <a name="the-events-tab"></a>[事件] 索引標籤

在偵錯工作階段期間，[診斷工具] 視窗的 [事件] 索引標籤會列出所發生診斷事件。 類別前置詞：**中斷點**、**檔案**和其他項目可讓您快速掃描清單中的類別，或略過不在意的類別。

請使用 [篩選] 下拉式清單，選取或取消選取事件的特定類別來篩選傳入和傳出檢視事件。

![診斷事件篩選](../profiling/media/diagnosticeventfilter.png "診斷事件篩選")

請使用搜尋方塊來尋找事件清單中的特定字串。 以下是搜尋字串 "name" 的結果，其符合四個事件：

![診斷事件搜尋](../profiling/media/diagnosticseventsearch.png "診斷事件搜尋")

如需詳細資訊，請參閱 [搜尋和篩選診斷工具視窗的事件索引標籤](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)。

## <a name="collect-profiling-data-without-debugging"></a>收集程式碼剖析資料但不偵錯

若要收集效能資料而不進行偵錯，您可以執行 [效能分析工具]。 某些分析工具需要系統管理員權限才能執行。 您可以系統管理員身分啟動 Visual Studio，或是在開始診斷工作階段時，以系統管理員身分執行這些工具。

1. 在 Visual Studio 中開啟專案後，請選取 [偵錯] > [效能分析工具]，或按 **Alt**+**F2**.

1. 在診斷啟動頁面上，選取要執行的一或多項工具。 只有適用於該專案類型、作業系統與程式設計語言的工具才會顯示。 選取 [顯示所有工具] 來另外查看針對這個診斷工作階段停用的工具。 如果是 C# UWP 應用程式，您的選擇會看起來如下：

   ![選取診斷工具](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. 若要開始診斷工作階段，請選取 [開始]。

   工作階段執行時，某些工具會在診斷工具啟動頁面上顯示即時資料圖表。

    ![在效能及診斷中樞上收集資料](../profiling/media/pdhub_collectdata.png "中樞收集資料")

1. 若要結束診斷工作階段，請選取 [停止收集]。

   已分析的資料會顯示在 [報表] 頁面上。

您可以儲存報表，並從診斷工具啟動頁面的 [最近開啟的工作階段] 清單中開啟這些報表。

![開啟已儲存的診斷工作階段檔案](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>程式碼剖析報表
 ![診斷工具報表](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![步驟 1](../profiling/media/procguid_1.png "ProcGuid_1")|時間軸會顯示程式碼剖析工作階段的長度、應用程式週期啟用事件，以及使用者標記。|
|![步驟 2](../profiling/media/procguid_2.png "ProcGuid_2")|您可以拖曳藍色巡覽列，選取時間軸的區域，將報告限制在時間軸的一部分。|
|![步驟 3](../profiling/media/procguid_3.png "ProcGuid_3")|每個診斷工具都會顯示一或多個主要圖表。 如果您的診斷工作階段有多個工具，則會顯示其所有主要圖表。|
|![步驟 4](../profiling/media/procguid_4.png "ProcGuid_4")|您可以摺疊和展開每個工具的個別圖表。|
|![步驟 5](../profiling/media/procguid_6.png "ProcGuid_6")|當資料包含一個以上的工具時，就會在這些索引標籤下收集工具的詳細資料。|
|![步驟 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|報表的後半部會顯示每個工具的一或多個詳細資料檢視。 您可以選取時間軸的區域來篩選檢視。|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>在已安裝或執行中的應用程式上執行診斷工作階段

 除了從 Visual Studio 專案啟動您的應用程式之外，您也可以在替代目標上執行診斷工作階段。 例如，建議您在從 Windows App Store 安裝的應用程式上診斷效能問題。

 ![選擇診斷工具分析目標](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 您可以啟動安裝的應用程式，也可以將診斷工具附加至已在執行中的應用程式和處理序。 當您選取 [執行中的應用程式] 或 [已安裝的應用程式] 時，您可以從所指定部署目標上找到的應用程式清單中選取應用程式。 這個目標可以是本機或遠端電腦。

 ![選擇診斷執行中或已安裝的應用程式](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>另請參閱

下列為診斷開發小組的部落格文章和 MSDN 文章：
- [MSDN Magazine：在 Visual Studio 2015 中進行偵錯時分析效能](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [MSDN Magazine：使用 IntelliTrace 更快速地診斷問題](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [部落格文章：Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/) (在 Visual Studio 2015 中使用記憶體使用量工具診斷事件處理常式流失)

- [影片：Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716) (在 Microsoft Visual Studio Ultimate 2015 中使用 IntelliTrace 進行歷程偵錯)

- [影片：Debugging Performance Issues Using Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731) (使用 Visual Studio 2015 對效能問題偵錯)

- [PerfTips:Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/) (效能提示：使用 Visual Studio 偵錯時的效能資訊一覽)

- [Visual Studio 2015 中的診斷工具偵錯工具視窗 (英文)](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [Visual Studio Enterprise 2015 中的 IntelliTrace (英文)](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
