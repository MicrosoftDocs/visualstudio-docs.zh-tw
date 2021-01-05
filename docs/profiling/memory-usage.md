---
title: 測量應用程式中的記憶體使用量
description: 當您進行偵錯時，您可以使用與偵錯工具整合的診斷工具，來找出記憶體流失和記憶體缺乏效率等問題。
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d259c6fa69821d1fecd26944227bff86cc82104
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815850"
---
# <a name="measure-memory-usage-in-visual-studio"></a>在 Visual Studio 中測量記憶體使用量

當您使用偵錯工具整合的 **記憶體使用量** 診斷工具進行偵錯工具時，找出記憶體流失和沒有效率的記憶體。 記憶體使用量工具可讓您擷取受控 原生之記憶體堆積的一或多個「快照」，以利了解物件類型的記憶體使用量影響。 您也可以在不附加偵錯工具的情況下分析記憶體使用量，或是以執行中的應用程式為目標。 如需詳細資訊，請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

除了可以在 **記憶體使用量** 工具中收集任何時間的記憶體快照之外，您還可以使用 Visual Studio 偵錯工具，來控制調查效能問題時要如何執行應用程式。 設定中斷點、逐步偵錯、全部中斷和其他偵錯工具動作，都可以協助您將效能調查工作集中在最相關的程式碼路徑上。 在應用程式執行時進行那些動作，可排除您不感興趣之程式碼的干擾，並可大幅縮短診斷問題所需的時間。

> [!Important]
> 偵錯工具整合的診斷工具支援在 Visual Studio 中進行 .NET 開發，包括 ASP.NET、ASP.NET Core、原生/c + + 開發和混合模式 ( .NET 和原生) 應用程式。 Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具] 視窗)。

在本教學課程中，您將：

> [!div class="checklist"]
> * 擷取記憶體的快照
> * 分析記憶體使用量資料

如果 **記憶體使用量** 未提供您所需的資料， [效能分析工具](../profiling/profiling-feature-tour.md#post_mortem) 中的其他程式碼剖析工具會提供可能對您有説明的不同種類資訊。 在許多情況下，您應用程式的效能瓶頸可能是因為記憶體（例如 CPU、轉譯 UI 或網路要求時間）以外的其他部分所造成。

> [!NOTE]
> **自訂** 配置器支援原生記憶體分析工具的運作方式是收集在執行時間所發出的配置 [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) 事件資料。  在來源層級已註釋 CRT 和 Windows SDK 中的配置器，以便擷取其配置資料。 如果您正在撰寫自己的配置器，則針對任何將指標傳回最新配置之堆積記憶體的函式，都可以使用 [__declspec](/cpp/cpp/declspec)(allocator) 來裝飾，如本範例中針對 myMalloc 所示：
>
> `__declspec(allocator) void* myMalloc(size_t size)`

## <a name="collect-memory-usage-data"></a>收集記憶體使用量資料

1. 開啟您想要在 Visual Studio 中偵錯的專案，並於應用程式中要開始檢查記憶體使用量的位置設定中斷點。

    如果您懷疑某個區域具有記憶體問題，請在記憶體問題發生之前設定第一個中斷點。

    > [!TIP]
    > 由於當應用程式頻繁地配置和解除配置記憶體時，擷取您感興趣之作業的記憶體設定檔可能會是項挑戰，因此請在作業開始和結束處 (或是逐項順著作業) 設定中斷點，以找出記憶體變更的實際點。

2. 在您想要分析的函式或程式碼區域結尾 (或是在可能的記憶體問題發生之後) 設定第二個中斷點。

3. 除非您已關閉 **診斷工具** 視窗，否則它會自動顯示。 若要再次顯示視窗，請按一下 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。

4. 以工具列上的 [選取工具] 設定選擇 [記憶體使用量]。

     ![顯示診斷工具](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. 按一下 [偵錯/開始偵錯] (或工具列上的 [開始] 或 **F5**)。

     當應用程式完成載入時，會出現 [Diagnostics Tools (診斷工具)] 的 [Summary (摘要)] 檢視。

     ![診斷工具摘要索引標籤](../profiling/media/diag-tools-summary-tab-2.png ">diagtoolssummarytab")

     > [!NOTE]
     > 由於收集記憶體資料可能會影響原生或混合模式應用程式的偵錯效能，因此預設會停用記憶體快照。 若要在原生或混合模式應用程式中啟用快照，請啟動偵錯工作階段 (快速鍵：**F5**)。 當 **診斷工具** 視窗出現時，選擇 [ **記憶體使用量** ] 索引標籤，然後選擇 [堆積程式碼 **剖析**]。
     >
     >  ![啟用快照集](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  停止 (快速鍵： **Shift** + **F5**) ，然後重新開機調試。

6. 若要在偵錯工作階段開始時擷取快照，請選擇 [記憶體使用量] 摘要工具列上的 [擷取快照]。 (在此設定中斷點也可能會有幫助)。

    ![拍攝快照集](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > 若要建立記憶體的比較基準，請考慮擷取偵錯工作階段開始時的快照。

6. 執行會叫用您的第一個中斷點的案例。

7. 當偵錯工具於第一個中斷點暫停時，選擇 [記憶體使用量] 摘要工具列上的 [擷取快照]。

8. 按 **F5** 使應用程式執行至第二個中斷點。

9. 現在請擷取另一個快照。

     此時，您可以開始分析資料。

## <a name="analyze-memory-usage-data"></a>分析記憶體使用量資料
[記憶體使用量] 摘要表的資料列會列出您在偵錯工作階段期間擷取的快照，並提供更詳細檢視的連結。

![記憶體摘要資料表](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 每個資料行的名稱則取決於您在專案屬性中選擇的偵錯模式：.NET、原生或混合 (.NET 和原生)。

- [物件 (差異)] 和 [配置數 (差異)] 資料行顯示擷取快照時 .NET 和原生記憶體中的物件數目。

- [堆積大小 (差異)] 資料行顯示 .NET 和原生堆積中的位元組數目

當您擷取多個快照之後，摘要表的資料格會包含資料列快照與上一個快照之間的值變更。

若要分析記憶體使用量，請按一下其中一個可以開啟記憶體使用量詳細報表的連結：

- 若要查看目前快照和上一個快照之間差異的詳細資料，請選擇箭號左邊的變更連結 (![記憶體使用量增加](../profiling/media/prof-tour-mem-usage-up-arrow.png "記憶體使用量增加")) 。 紅色箭號表示記憶體使用量增加，綠色箭號表示減少。

> [!TIP]
> 為了協助使用者更快速地識別記憶體問題，差異報表會以整體數目增加最多 (按一下 [物件 (差異)] 資料行中的變更連結)，或整體堆積大小增加最多 (按一下 [堆積大小 (差異)] 資料行中的變更連結) 的物件類型來分類。

- 若只要檢視所選快照的詳細資料，請按一下未變更連結。

   報表會在個別的視窗中顯示。

### <a name="managed-types-reports"></a>Managed 類型報表
 選擇 [記憶體使用量] 摘要表中 [物件 (差異)] 或 [配置數 (差異)] 資料格的目前連結。

 ![偵錯工具管理型別報表 &#45; 根目錄的路徑](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 上方窗格顯示快照中所有類型的計數和大小，包括類型參考之所有物件的大小 ([內含大小])。

 下方窗格中的 [根的路徑]  樹狀結構顯示參考在上方窗格中選取之類型的物件。 .NET 垃圾收集行程只會在參考物件的最後一個類型已釋放時，清除物件的記憶體。

 [ **參考的物件** ] 樹狀目錄會顯示在上方窗格中選取之類型所持有的參考。

 ![Managed 參考物件報表檢視](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 若要在上方窗格中顯示所選類型的實例，請選擇 ![實例圖示](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") 圖示。

 ![[記憶體使用量] 工具 Visual Studio 中 [實例] 視圖的螢幕擷取畫面，其中顯示 [實例] 窗格和 [根的路徑] 和 [參考的物件] 窗格。](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 [執行個體]  檢視顯示在上方窗格的快照中選取之物件的執行個體。 [根的路徑] 和 [參考的物件] 窗格顯示參考所選執行個體的物件，以及所選執行個體參考的類型。 當偵錯工具在建立快照集的時間點停止時，您可以將滑鼠停留在 [ **值** ] 資料格上方，以在工具提示中顯示物件的值。

### <a name="native-type-reports"></a>原生類型報表
 在 [診斷工具] 視窗的 [記憶體使用量] 摘要表中，選擇 [配置數 (差異)] 或 [堆積大小 (差異)] 資料格的目前連結。

 ![原生類型檢視](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 [類型檢視]  顯示快照中所有類型的數目和大小。

- 選擇 [實例] 圖示 (所選類型 ![的 [物件類型] 資料行) 中的實例圖示](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon") ，以顯示快照中所選類型的物件相關資訊。

     [執行個體]  檢視顯示所選類型的每個執行個體。 選取執行個體會顯示在 [配置呼叫堆疊]  窗格中建立執行個體時所產生的呼叫堆疊。

     ![[Visual Studio 記憶體使用量] 工具中 [實例] 視圖的螢幕擷取畫面，其中顯示 [實例] 窗格和 [配置呼叫堆疊] 窗格。](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- 在 [檢視模式]  清單中選擇 [堆疊檢視]  ，以查看所選類型的配置堆疊。

     ![堆疊檢視](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>變更 (差異比對) 報表

- 在 [診斷工具]  視窗中，選擇 [記憶體使用量]  索引標籤摘要表資料格中的變更連結。

   ![選擇變更 &#40;差異&#41; 報表](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- 在 Managed 或原生報表的 [比較]  清單中，選擇一個快照。

   ![從 [比較] 清單中選擇快照集](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

變更報表會將顯示基礎快照值與比較快照之間有差異的資料行 (標記為 [(差異比對)] )，加入基礎報表。 以下是原生類型檢視差異比對報表可能的樣子：

![原生類型差異視圖](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>部落格和影片

[Analyze CPU and Memory While Debugging](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/) (偵錯時分析 CPU 與記憶體)

[Visual C++ Blog: Memory Profiling in Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/) (Visual C++ 部落格：Visual C++ 2015 中的記憶體分析)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何收集並分析記憶體使用量資料。 如果您已完成[分析工具的教學課程](../profiling/profiling-feature-tour.md)，建議您快速查看如何分析應用程式的 CPU 使用量。

> [!div class="nextstepaction"]
> [分析 CPU 使用量](../profiling/beginners-guide-to-performance-profiling.md)
