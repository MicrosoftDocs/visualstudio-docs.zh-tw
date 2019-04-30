---
title: 記憶體使用量 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 437e541fab1559c65c410d94a8911c158aa3592e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438926"
---
# <a name="memory-usage"></a>記憶體使用量
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您進行偵錯時，您可以使用與偵錯工具整合的 **記憶體使用量** 診斷工具，來找出記憶體遺漏和記憶體使用沒有效率等問題。 記憶體使用量工具可讓您擷取 Managed 和原生記憶體堆積的一個或多個 *「快照」* (Snapshot)。 您可以收集 .NET、原生或混合模式 (.NET 和原生) 應用程式的快照。  
  
- 您可以分析一份快照，了解物件類型對於記憶體使用的相對影響，並找出應用程式中無效率使用記憶體的程式碼。  
  
- 您也可以比較 (差異比對) 應用程式的兩個快照，找出造成記憶體使用量隨著時間逐漸增加的程式碼部分。  
  
  下圖顯示 Visual Studio 2015 Update 1 中的 [診斷工具]  視窗：  
  
  ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
  除了可以在 **記憶體使用量** 工具中收集任何時間的記憶體快照之外，您還可以使用 Visual Studio 偵錯工具，來控制調查效能問題時要如何執行應用程式。 設定中斷點、逐步偵錯、全部中斷和其他偵錯工具動作，都可以協助您將效能調查工作集中在最相關的程式碼路徑上。 在應用程式執行時進行這些動作，可排除您不感興趣之程式碼的干擾，並可大幅縮短診斷問題所需的時間。  
  
  您也可以在偵錯工具外部使用記憶體工具。 請參閱 [Memory Usage without Debugging](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0)。  
  
> [!NOTE]
> **自訂配置器支援** 原生記憶體分析工具的運作方式是收集在執行階段所發出的配置 [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) 事件資料。  在來源層級已註釋 CRT 和 Windows SDK 中的配置器，以便擷取其配置資料。  如果您正在撰寫自己的配置器，傳回新剛剛配置之堆積記憶體指標的任何函式，都可以使用 [__declspec](http://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(配置器) 裝飾，如 myMalloc 本範例所示：  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>使用偵錯工具分析記憶體使用量  
  
> [!NOTE]
> 由於收集記憶體資料可能會影響原生或混合模式應用程式的偵錯效能，因此預設會停用記憶體快照。 若要啟用原生或混合式應用程式的快照，開始偵錯工作階段 (快速鍵：**F5**)。 在顯示 [診斷工具]  視窗時，選擇 [記憶體使用量] 索引標籤，然後選擇 [啟用快照] 。  
>   
> ![啟用快照](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> 停止 (快速鍵：**Shift + F5**)，然後重新啟動偵錯。  
  
 每當您想要擷取記憶體的狀態時，請選擇 [記憶體使用量]  摘要工具列上的 [擷取快照]  。  
  
 ![擷取快照](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - 若要建立記憶體的比較基準，請考慮擷取偵錯工作階段開始時的快照。  
>   - 由於當應用程式頻繁地配置和解除配置記憶體時，擷取您感興趣之作業的記憶體設定檔可能會是項挑戰，因此請在作業開始和結束處設定中斷點，或逐步執行作業，以找出記憶體變更的實際點。  
  
## <a name="viewing-memory-snapshot-details"></a>檢視記憶體快照詳細資料  
 記憶體使用量摘要表的資料列會列出您在偵錯工作階段期間擷取的快照。  
  
 每個資料列的資料行則取決於您在專案屬性中選擇的偵錯模式：.NET、原生或混合 (.NET 和原生)。  
  
- [Managed 物件] 和 [原生配置]  資料行顯示擷取快照時 .NET 和原生記憶體中的物件數目。  
  
- [Managed 堆積大小]  和 [原生堆積大小]  資料行顯示 .NET 和原生堆積中的位元組數目。  
  
- 當您擷取多個快照之後，摘要表的資料格會包含資料列快照與上一個快照之間的值變更。  
  
   ![記憶體摘要表儲存格](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **檢視詳細資料報表：**  
  
- 若只要檢視所選快照的詳細資料，請選擇目前連結。  
  
- 若要檢視目前快照與上一個快照之間的差異詳細資料，請選擇變更連結。  
  
  報表會在個別的視窗中顯示。  
  
## <a name="memory-usage-details-reports"></a>記憶體使用量詳細資料報表  
  
### <a name="managed-types-reports"></a>Managed 類型報表  
 選擇記憶體使用量摘要表中 [Managed 物件]  或 [Managed 堆積大小]  資料格的目前連結。  
  
 ![偵錯工具 Managed 類型報表 &#45; 根的路徑](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 上方窗格顯示快照中所有類型的計數和大小，包括類型參考之所有物件的大小 ([內含大小])。  
  
 下方窗格中的 [根的路徑]  樹狀結構顯示參考在上方窗格中選取之類型的物件。 您必須釋放參考物件的最後一個類型，.NET Framework 記憶體回收行程才會清除該物件的記憶體。  
  
 [參考的類型]  樹狀結構顯示在上方窗格中選取之類型所持有的參考。  
  
 ![Managed 參考的類型報表檢視](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 若要在上方窗格中顯示所選取類型的執行個體，請選擇 ![執行個體圖示](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") 圖示。  
  
 ![執行個體檢視](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 [執行個體]  檢視顯示在上方窗格的快照中選取之物件的執行個體。 [根的路徑] 和 [參考的物件] 窗格顯示參考所選執行個體的物件，以及所選執行個體參考的類型。 當偵錯工具在擷取快照的位置停止時，您可以將滑鼠停留在 [值] 資料格，以在工具提示中顯示物件的值。  
  
### <a name="native-type-reports"></a>原生類型報表  
 在 [診斷工具]  視窗的記憶體使用量摘要表中，選擇 [原生配置]  或 [原生堆積大小]  資料格的目前連結。  
  
 ![原生類型檢視](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 [類型檢視]  顯示快照中所有類型的數目和大小。  
  
- 選擇所選取類型的執行個體圖示 (![[物件類型] 欄中的執行個體圖示](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon"))，以顯示快照中所選取類型的物件相關資訊。  
  
     [執行個體]  檢視顯示所選類型的每個執行個體。 選取執行個體會顯示在 [配置呼叫堆疊]  窗格中建立執行個體時所產生的呼叫堆疊。  
  
     ![執行個體檢視](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- 在 [檢視模式]  清單中選擇 [堆疊檢視]  ，以查看所選類型的配置堆疊。  
  
     ![堆疊檢視](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>變更 (差異比對) 報表  
  
- 在 [診斷工具]  視窗中，選擇 [記憶體使用量]  索引標籤摘要表資料格中的變更連結。  
  
   ![選擇變更 &#40;差異&#41; 報表](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- 在 Managed 或原生報表的 [比較]  清單中，選擇一個快照。  
  
   ![從 [比較] 清單中選擇快照](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  變更報表會將顯示基礎快照值與比較快照之間有差異的資料行 (標記為 [(差異比對)] )，加入基礎報表。 以下是原生類型檢視差異比對報表可能的樣子：  
  
  ![原生類型差異檢視](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>部落格和影片  
 [Visual Studio 2015 中的診斷工具偵錯工具視窗 (英文)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [部落格：在 Visual Studio 2015 中偵錯時的記憶體使用量工具](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/13/memory-usage-tool-while-debugging-in-visual-studio-2015.aspx)  
  
 [Visual C++ 部落格：VS2015 Preview 中的原生記憶體診斷](http://blogs.msdn.com/b/vcblog/archive/2014/11/21/native-memory-diagnostics-in-vs2015-preview.aspx)  
  
 [Visual C++ 部落格：Visual Studio 2015 CTP 的原生記憶體診斷工具](http://blogs.msdn.com/b/vcblog/archive/2014/06/04/native-memory-diagnostic-tools-for-visual-studio-14-ctp1.aspx)
