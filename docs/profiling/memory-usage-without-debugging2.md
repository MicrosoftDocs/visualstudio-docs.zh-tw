---
title: 分析效能分析工具中的記憶體使用量
description: 瞭解如何在 Visual Studio 效能分析工具中使用記憶體使用量工具，而不使用偵錯工具來監視應用程式的記憶體使用量。
ms.custom: ''
ms.date: 04/02/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ac088d52b4e7a288965bb75e1bc6a00da40f7b
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815811"
---
# <a name="analyze-memory-usage-without-debugging-in-the-performance-profiler"></a>在效能分析工具中分析記憶體使用量，而不進行調試

[記憶體使用量] 工具會監視您的應用程式記憶體使用量。 您可以使用此工具，在 Visual Studio 中研究積極開發中案例的即時記憶體效果。 您可以建立詳細的應用程式記憶體狀態快照，並比較快照以找出記憶體問題的根本原因。 .NET、ASP.NET、c + + 或混合模式支援記憶體使用量工具 ( .NET 和原生) 應用程式。

記憶體使用量工具可以 [使用或不使用偵錯工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)來執行。 在本文中，我們將示範如何在 Visual Studio **效能分析工具** 中使用記憶體使用量工具，而不使用偵錯工具，這是發行組建的建議。

## <a name="memory-usage-diagnostic-sessions"></a>[記憶體使用量] 診斷工作階段

**開始 [記憶體使用量] 診斷工作階段：**

1. 在 Visual Studio 中開啟專案。

   記憶體使用量工具支援 .net、ASP.NET、c + + 或混合模式 ( .NET 和原生) 應用程式。

1. 在 [偵錯工具] 功能表中，將 [方案設定] 設定為 [ **發行** ]，然後選取 [ **本機 Windows 偵錯工具** (] 或 [ **本機電腦**) 作為部署目標。

1. 在功能表列上，選擇 [ **Debug**  >  **效能分析工具**]。

1. 在 [ **可用的工具**] 底下，選取 [ **記憶體使用量**]，然後選取 [ **啟動**]。

   ![開始記憶體使用量診斷工作階段](../profiling/media/memuse_start_diagnosticssession.png "開始記憶體使用量診斷工作階段")

### <a name="monitor-memory-use"></a>監視記憶體使用情況

當您開始診斷會話時，您的應用程式會啟動，且 **診斷工具** 視窗會顯示應用程式記憶體使用量的時間軸圖形。

![Visual Studio 效能分析工具中的 [診斷工具] 視窗的螢幕擷取畫面，其中顯示應用程式記憶體使用量的時間軸圖形。](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

時間軸圖形會在應用程式執行時顯示記憶體波動。 圖形中的高峰通常表示一些程式碼正在收集或建立資料，然後在處理完成時將它捨棄。 大型的高峰表示您可能可以最佳化的區域。 更值得關注的是未傳回的記憶體耗用提高，因為它可能表示記憶體使用效率低落，或甚至是記憶體流失。

### <a name="take-snapshots-of-app-memory-states"></a>擷取應用程式記憶體狀態的快照

應用程式會使用大量的物件，您可能會想專注分析單一案例。 或者，您可能會發現要調查的記憶體問題。 您可以在診斷工作階段期間擷取快照，以便擷取特定時刻的記憶體使用量。 在記憶體問題出現之前先取得基準快照、第一次出現問題之後擷取另一張快照，且如果您能重複案例便再額外擷取快照，這是不錯的做法。

若要收集快照，當您想要擷取記憶體資料時，請選取 [擷取快照]。

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a> 關閉診斷工作階段

若要停止監控工作階段而不建立報表，只需關閉診斷視窗。 當您完成時收集或擷取快照時若要產生報表，請選取 [停止收集]。

![停止收集](../profiling/media/memuse__stopcollection.png "停止收集")

## <a name="memory-usage-reports"></a>[記憶體使用量] 報表

停止資料收集之後，[記憶體使用量] 工具會停止應用程式，並顯示 [記憶體使用量] 概觀報表。

![[記憶體使用量] 工具效能分析工具 Visual Studio 中 [記憶體使用量] 工具的 [總覽] 頁面的螢幕擷取畫面，其中顯示記憶體使用量圖表和兩個快照窗格。](../profiling/media/memuse__reportoverview1.png "記憶體使用量概觀頁面")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> [記憶體使用量] 快照

[快照] 窗格中的數字顯示擷取每個快照時，記憶體中的位元組和物件，以及快照與上一個快照之間的差異。

數字是連結，其會在新的 Visual Studio 視窗中開啟詳細的 [記憶體使用量] 報表檢視。 [快照詳細資料報表](#snapshot-details-reports)顯示一張快照中的類型和執行個體。 [快照差異 (diff) 報表](#snapshot-difference-diff-reports)會比較兩張快照的類型和執行個體。

  ![快照檢視連結](../profiling/media/memuse__snapshotview_numbered.png "快照檢視連結")

|映像|描述|
|-|-|
|![步驟 1](../profiling/media/procguid_1.png "ProcGuid_1")|在擷取快照時，記憶體中的總位元組數。<br /><br /> 選取這個連結可以顯示快照詳細資料報表，此報表依類型執行個體的大小總計進行排序。|
|![步驟 2](../profiling/media/procguid_2.png "ProcGuid_2")|在擷取快照時，記憶體中的物件總數。<br /><br /> 選取這個連結可以顯示快照詳細資料報表，此報表依類型執行個體的計數進行排序。|
|![步驟 3](../profiling/media/procguid_3.png "ProcGuid_3")|此快照中記憶體物件與上一個快照物件之大小總計之間的差異。 <br /><br /> 正數表示此快照的記憶體大小大於與上一個快照，負數則表示大小較小。 **基準** 表示快照是診斷工作階段中的第一個。 **無任何差異** 表示差異為零。<br /><br /> 選取這個連結可以顯示快照差異報表，此報表依執行個體類型的大小總計差異進行排序。|
|![步驟4](../profiling/media/procguid_4.png "ProcGuid_4")|此快照中的記憶體物件與上一個快照物件總數之間的差異。<br /><br /> 選取這個連結可以顯示快照差異報表，此報表依執行個體類型的總計數差異進行排序。|

## <a name="memory-usage-snapshot-reports"></a>[記憶體使用量] 快照報表

<a name="BKMK_Snapshot_report_trees"></a> 當您選取 [記憶體使用量] 概觀頁面中的其中一個快照連結時，會在新的頁面開啟快照報表。

![記憶體使用量快照報表](../profiling/media/memuse_snapshotreport_all.png "記憶體使用量快照報表")

您可以在快照報表中，展開 [物件類型] 項目，以顯示子項目。 執行個體名稱是由 [記憶體使用量] 工作所產生的唯一識別碼。

如果 [物件類型] 是藍色，則您可以選取它以在個別視窗中巡覽至原始程式碼中的物件。

您無法識別的型別，或是您不了解的程式碼介入可能是 .NET、作業系統或編譯器物件。 [記憶體使用量] 工具會顯示這些物件，如果它們參與您物件的擁有權鏈結。

在快照報表中：

- [受控堆積] 樹狀結構顯示報表中的類型和執行個體。 選取類型或執行個體會顯示選取項目的 [根的路徑] 和 [參考的物件] 樹狀目錄。

- [ **根的路徑** ] 樹狀結構會顯示參考類型或實例的物件鏈。 .NET 垃圾收集行程只會在對物件的所有參考都已釋放時才清除物件的記憶體。

- [參考的類型] 或 [參考的物件] 樹狀結構顯示所選取類型或執行個體參考的物件。

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a>報表樹狀目錄篩選條件

在應用程式中，有許多類型對於應用程式開發人員而言不是非常有趣。 快照報表篩選條件可以在 [受控堆積] 和 [根的路徑] 樹狀結構中，隱藏這些類型的大部分。

![排序和篩選選項](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a> 若要依類型名稱來篩選樹狀結構，請在 [篩選條件] 方塊中輸入名稱。 篩選條件不會區分大小寫，且它會辨識類型名稱任何部分中的指定字串。

- <a name="BKMK_Collapse_Small_Objects"></a> 選取 [篩選條件] 下拉式清單中的 [摺疊小物件]，隱藏 [大小 (位元組)] 小於總記憶體 0.5% 的類型。

- <a name="BKMK_Just_My_Code"></a> 選取 [篩選條件] 下拉式清單中的 [Just My Code]，隱藏外部程式碼所產生的大部分執行個體。 外部類型屬於作業系統或架構元件，或者由編輯器產生。

## <a name="snapshot-details-reports"></a>快照詳細資料報表

 快照詳細資料報表描述診斷工作階段的一張快照。 若要開啟報表，請選取快照窗格中的大小或物件連結。

 ![快照窗格中的快照報表連結](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "快照窗格中的快照報表連結")

兩個連結都會開啟相同的報表。 唯一的差別在於 [受控堆積] 樹狀結構的起始排序次序。 大小連結會依據 [內含大小 (位元組)] 資料行來排序報表。 物件連結會依據 [計數] 資料行來排序報表。 您可以在報表開啟之後變更排序資料行或次序。

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> [受控堆積] 樹狀結構 (快照詳細資料報表)
 [Managed 堆積] 樹狀目錄會列出保留在記憶體中的物件類型。 展開類型名稱，即可檢視依大小排序的前十大類型執行個體。 選取類型或執行個體會顯示選取項目的 [根的路徑] 和 [參考的物件] 樹狀結構。

 ![Managed 堆積樹狀](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Managed 堆積樹狀")

快照詳細資料報表中的 [受控堆積] 樹狀結構有下列資料行：

|名稱|描述|
|-|-|
|**物件類型**|類型或物件執行個體的名稱。|
|**Count**|類型的物件執行個體數目。 一個執行個體的 [計數] 一律為 1。|
|**(位元組大小)**|針對類型，此為快照中類型的所有執行個體大小，減去執行個體中包含的物件大小。<br /><br /> 針對執行個體，此為物件的大小，減去執行個體中包含的物件大小。 |
|**內含大小 (位元組)**|類型執行個體的大小，或是單一執行個體的大小，且包括所包含物件的大小。|
|**模組**|包含物件的模組。|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> [根的路徑] 樹狀結構 (快照詳細資料報表)
[根的路徑] 樹狀結構顯示參考類型或執行個體的物件鏈結。 .NET 垃圾收集行程只會在對物件的所有參考都已釋放時才清除物件的記憶體。

針對 [根的路徑] 樹狀結構中的類型，會在 [參考計數] 資料行顯示保有該類型參考的物件數目。

![類型的根樹狀路徑](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "類型的根樹狀路徑")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> [參考的類型] 或 [參考的物件] 樹狀結構 (快照詳細資料報表)
[參考的類型] 或 [參考的物件] 樹狀結構顯示所選取類型或執行個體參考的物件。

![實例的參考物件樹狀結構](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "實例的參考物件樹狀結構")

快照詳細資料報表中的 [參考的類型] 樹狀結構有下列資料行。 [參考的物件] 樹狀結構沒有 [參考計數] 資料行。

|名稱|描述|
|-|-|
|**物件類型** 或 **執行個體**|類型或執行個體的名稱。|
|**參考計數**|針對類型，此為類型的物件執行個體數目。|
|**(位元組大小)**|針對類型，此為類型的所有執行個體大小，減去類型中包含的物件大小。<br /><br /> 針對執行個體，此為物件的大小，減去物件中包含的物件大小。|
|**內含大小 (位元組)**|類型執行個體的大小總計，或是執行個體的大小，且包括所包含物件的大小。|
|**模組**|包含物件的模組。|

## <a name="snapshot-difference-diff-reports"></a>快照差異 (diff) 報表

快照差異 (diff) 報表會顯示主要快照與在它之前快照之間的變更。 若要開啟差異報表，請在快照窗格中選取其中一個差異連結。

兩個連結都會開啟相同的報表。 唯一的差別在於報表中 [受控堆積] 樹狀結構的起始排序次序。 大小連結會依據 [內含大小差異 (位元組)] 資料行來排序報表。 物件連結會依據 [計數差異] 資料行來排序報表。 您可以在報表開啟之後變更排序資料行或次序。

 ![快照窗格中的差異報表連結](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "快照窗格中的差異報表連結")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> [受控堆積] 樹狀結構 (快照差異報表)

 [Managed 堆積] 樹狀目錄會列出保留在記憶體中的物件類型。 您可以展開類型名稱，檢視依大小排序的前十大類型執行個體。 選取類型或執行個體會顯示選取項目的 [根的路徑] 和 [參考的物件] 樹狀結構。

 ![不同報表中類型的 Managed 堆積樹狀結構](../profiling/media/memuse_snapshotdiff_type_heap.png "不同報表中類型的 Managed 堆積樹狀結構")

快照差異報表中的 [受控堆積] 樹狀結構有下列資料行：

|名稱|描述|
|-|-|
|**物件類型**|類型或物件執行個體的名稱。|
|**Count**|主要快照中類型的執行個體數目。 實例的 **計數** 一律為1。|
|**計數差異**|對於類型，此為主要快照和上一個快照中的類型執行個體數目差異。 執行個體的欄位空白。|
|**(位元組大小)**|主要快照中的物件大小，減去物件中包含的物件大小。 對於類型，[大小 (位元組)] 和 [內含大小 (位元組)] 是類型執行個體的大小總計。|
|**總大小差異 (位元組)**|針對類型，此為主要快照與上一個快照之間，類型的執行個體大小總計，減去執行個體中的物件大小。 執行個體的欄位空白。|
|**內含大小 (位元組)**|主要快照中的物件大小，包括物件中的物件大小。|
|**內含大小差異 (位元組)**|針對類型，此為主要快照與上一個快照之間，類型的所有執行個體大小差異，包括物件中的物件大小。 執行個體的欄位空白。|
|**模組**|包含物件的模組。|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> [根的路徑] 樹狀結構 (快照差異報表)

[根的路徑] 樹狀結構顯示參考類型或執行個體的物件鏈結。 .NET 垃圾收集行程只會在對物件的所有參考都已釋放時才清除物件的記憶體。

針對 [根的路徑] 樹狀結構中的類型，會在 [參考計數] 資料行顯示保有該類型參考的物件數目。 與上一個快照的計數差異位在 [參考差異] 資料行中。

 ![差異報表中的根路徑樹狀結構](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "差異報表中的根路徑樹狀結構")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> [參考的類型] 或 [參考的物件] 樹狀結構 (快照差異報表)

[參考的類型] 或 [參考的物件] 樹狀結構顯示所選取類型或執行個體參考的物件。

![差異報表中的參考類型](../profiling/media/memuse_snapshotdiff_referencedtypes.png "差異報表中的參考類型")

快照差異報表中的 [參考的類型] 樹狀結構有下列資料行。 [參考的物件] 樹狀結構有 [執行個體]、[大小 (位元組)]、[內含大小 (位元組)]和 [模組] 資料行。

|名稱|描述|
|-|-|
|**物件類型** 或 **執行個體**|類型或物件執行個體的名稱。|
|**參考計數**|主要快照中類型的執行個體數目。|
|**參考計數差異**|對於類型，此為主要快照和上一個快照中的類型執行個體數目差異。|
|**(位元組大小)**|主要快照中的物件大小，減去物件中包含的物件大小。 對於類型，[大小 (位元組)] 和 [內含大小 (位元組)] 是類型執行個體的大小總計。|
|**總大小差異 (位元組)**|針對類型，此為主要快照與上一個快照之間，類型的執行個體大小總計，減去執行個體中的物件大小。 |
|**內含大小 (位元組)**|主要快照中的物件大小，包括物件中的物件大小。|
|**內含大小差異 (位元組)**|針對類型，此為主要快照與上一個快照之間，類型的所有執行個體大小差異，包括物件中的物件大小。|
|**模組**|包含物件的模組。|

## <a name="see-also"></a>請參閱
- [JavaScript 記憶體](../profiling/javascript-memory.md)
- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)
- [使用 C++、C# 及 Visual Basic 的 UWP App 效能最佳做法](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [使用 Visual Studio 中的新記憶體使用量工具來診斷記憶體問題](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)