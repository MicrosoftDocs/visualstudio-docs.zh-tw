---
title: 分析 .NET Framework 的記憶體問題 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295893"
---
# <a name="analyze-net-framework-memory-issues"></a>分析 .NET Framework 記憶體問題
使用 Visual Studio Managed 記憶體分析器，找出 .NET Framework 程式碼中記憶體流失和記憶體使用沒有效率的問題。 目標程式碼的最小 .NET Framework 版本是 .NET Framework 4.5。  
  
 記憶體分析工具會分析傾印檔案中的資訊，以及應用程式記憶體中物件複本的*堆積資料*。 您可以從 Visual Studio IDE 或透過其他系統工具收集傾印檔案 (.dmp)。  
  
- 您可以分析一份快照，了解物件類型對於記憶體使用的相對影響，並找出應用程式中無效率使用記憶體的程式碼。  
  
- 您也可以比較（*diff*）應用程式的兩個快照，以找出程式碼中造成記憶體使用量隨著時間增加的區域。  
  
  如需 managed 記憶體分析器的逐步解說，請參閱 Visual Studio ALM + Team Foundation Server blog[中的使用 Visual Studio 2013 診斷生產環境中的 .Net 記憶體問題](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)。  
  
## <a name="BKMK_Contents"></a> 內容  
 [.NET Framework 應用程式中的記憶體使用量](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [找出應用程式中的記憶體問題](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [收集記憶體快照集](#BKMK_Collect_memory_snapshots)  
  
 [分析記憶體使用量](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a>.NET Framework 應用程式中的記憶體使用量  
 .NET Framework 是記憶體回收執行階段，因此在大多數應用程式中，記憶體使用情況不會構成問題。 但在長時間執行的應用程式 (例如 Web 服務和應用程式) 及記憶體數量有限的裝置中，記憶體中累積的物件會對應用程式及應用程式執行所在的裝置造成效能影響。 如果記憶體回收行程太常執行，或者強制作業系統在 RAM 和磁碟之間移動記憶體，則會過度使用記憶體，而導致應用程式和資源所在的電腦記憶體不足。 在最糟的情況下，應用程式可能會損毀並出現「記憶體不足」的例外狀況。  
  
 .NET*受控堆積*是虛擬記憶體的區域，其中會儲存應用程式所建立的參考物件。 物件的存留期是由記憶體回收行程 (GC) 所管理。 記憶體回收行程使用參考來追蹤佔用記憶體區塊的物件。 當系統建立物件並指派給變數時，便會建立參考。 一個物件可以有多個參考。 例如，您可以將物件加入至類別、集合或其他資料結構，或者將物件指派給第二個變數，來建立物件的其他參考。 還有一個較不常見的建立參考方式，那就是由某個物件將處理常式加入至另一個物件的事件。 在此情況下，第二個物件會保留第一個物件的參考，直到明確移除處理常式或終結第二個物件為止。  
  
 GC 針對每個應用程式維護一個參考樹狀目錄，以追蹤應用程式參考的物件。 *參考樹狀結構*具有一組根，其中包含全域和靜態物件，以及相關聯的執行緒堆疊和動態具現化的物件。 如果某個物件至少有一個參考該物件的父物件，則該物件是根目錄。 只有應用程式中沒有其他物件或變數參考該物件時，GC 才能回收該物件的記憶體。  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a>找出應用程式中的記憶體問題  
 應用程式效能是記憶體問題的最明顯徵兆，特別是效能隨著時間逐漸降低時。 如果您的應用程式執行期間有其他應用程式的效能降低，也表示發生記憶體問題。 如果您懷疑發生記憶體問題，請使用工作管理員或[Windows 效能監視器](https://technet.microsoft.com/library/cc749249.aspx)之類的工具來進一步調查。 例如，尋找您無法解釋的記憶體大小總計成長量，當做記憶體流失的可能來源：  
  
 ![資源監視器中的一致記憶體成長](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 您也可能注意到那些遠超出您所認為程式碼應該使用的記憶體量增量，這可能指出某個程序的記憶體使用沒有效率：  
  
 ![Resource Manager 中的記憶體尖峰](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a>收集記憶體快照集  
 記憶體分析工具會分析包含堆積*資訊的傾*印檔案中的資訊。 您可以在 Visual Studio 中建立傾印檔案，也可以使用[ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) From [Windows Sysinternals](https://technet.microsoft.com/sysinternals)之類的工具。 請參閱 Visual Studio 偵錯工具小組 blog 上[的什麼是傾印和如何建立它？](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) 。  
  
> [!NOTE]
> 大多數工具都可以收集含有或不含堆積記憶體資料的傾印資訊。 Visual Studio 記憶體分析器需要完整的堆積資訊。  
  
 **從 Visual Studio 收集傾印**  
  
1. 您可以建立從 Visual Studio 專案啟動之處理序的傾印檔案，也可以將偵錯工具附加至執行中的處理序。 請參閱[附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。  
  
2. 停止執行。 當您選擇 [**調試**程式] 功能表上的 [**全部中斷**] 時，或在例外狀況或中斷點時，偵錯工具會停止  
  
3. 在 [**調試**] 功能表上，選擇 [**另存**傾印]。 在 [**另存**傾印] 對話方塊中，指定一個位置，並確定已在 [**存檔類型**] 清單中選取 [**使用堆積的小型**傾印（預設值）]。  
  
   **比較兩個記憶體快照集**  
  
   若要分析應用程式的記憶體使用成長量，請從一個應用程式執行個體收集兩個傾印檔案。  
  
   ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a>分析記憶體使用量  
 [篩選](#BKMK_Filter_the_list_of_objects) **&#124;** [從單一快照](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** 集來分析記憶體資料的物件清單[比較兩個記憶體快照](#BKMK_Compare_two_memory_snapshots)集  
  
 若要分析傾印檔案以找出記憶體使用問題：  
  
1. 在 Visual Studio 中，**選擇 [** 檔案]，**開啟**並指定傾印檔案。  
  
2. 在 [**小型**傾印檔案摘要] 頁面上，選擇 [**調試 Managed 記憶體**]。  
  
    ![傾印檔案摘要頁面](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   記憶體分析器會啟動偵錯工作階段以分析檔案，並在 [堆積檢視] 頁面中顯示結果：  
  
   ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a>篩選物件清單  
 根據預設，記憶體分析器會篩選記憶體快照中的物件清單，只顯示使用者程式碼的類型和執行個體，並且只顯示內含大小總計超過堆積大小總計之臨界值百分比的類型。 您可以在 [**查看設定**] 清單中變更這些選項：  
  
|||  
|-|-|  
|**啟用 Just My Code**|Just My Code 隱藏最常見的系統物件，只在清單中顯示您建立的類型。<br /><br /> 您也可以在 [Visual Studio**選項**] 對話方塊中設定 [Just My Code] 選項。 在 [ **偵錯** ] 功能表上選擇 [ **選項和設定**]。 在 [**調試**/**一般**] 索引標籤中，選擇或清除 [ **Just My Code**]。|  
|**折迭小型物件**|[折迭**小型物件**] 會隱藏所有內含大小總計小於堆積大小總計0.5% 的所有類型。|  
  
 您也可以在 [**搜尋**] 方塊中輸入字串，以篩選類型清單。 此清單只會顯示其名稱包含字串的類型。  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>從單一快照集分析中的記憶體資料  
 Visual Studio 啟動新的偵錯工作階段以分析檔案，並在 [堆積檢視] 視窗中顯示記憶體資料。  
  
 ![[物件類型] 清單](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>物件類型資料表  
 上方資料表列出保留在記憶體中之物件的類型。  
  
- [**計數**] 顯示快照中類型的實例數目。  
  
- [**大小（位元組）** ] 是類型的所有實例大小，但不包括其持有參考的物件大小。 該  
  
- [**內含大小（位元組）** ] 包含參考物件的大小。  
  
  您可以選擇 [**物件類型**] 資料行中的實例圖示（[![物件類型] 資料行中的實例圖示](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")），以查看該類型實例的清單。  
  
#### <a name="instance-table"></a>執行個體資料表  
 ![實例資料表](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **實例**是物件的記憶體位置，作為物件的物件識別碼。  
  
- [**值**] 顯示實數值型別的實際值。 您可以將滑鼠指標停留在參考類型的名稱上，以在資料提示中檢視其資料值。  
  
   ![資料提示中的實例值](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- [**大小（位元組）** ] 是物件的大小，但不包括其持有參考的物件大小。 該  
  
- [**內含大小（位元組）** ] 包含參考物件的大小。  
  
  根據預設，類型和實例會依 **[內含大小（位元組）** ] 排序。 選擇清單中的資料行標頭可變更排序次序。  
  
#### <a name="paths-to-root"></a>根目錄路徑  
  
- 針對從 [**物件類型**] 資料表中選取的類型，[**根的路徑**] 資料表會顯示唯一的類型階層，這些階層會導致該類型之所有物件的根物件，以及階層中其上方類型的參考數目。  
  
- 針對從類型實例中選取的物件，[**根的路徑**] 會顯示保存該實例之參考的實際物件圖形。 您可以將滑鼠指標停留在物件的名稱上，以在資料提示中檢視其資料值。  
  
#### <a name="referenced-types--referenced-objects"></a>參考的類型/參考的物件  
  
- 針對從 [**物件類型**] 資料表中選取的類型，[**參考的類型**] 索引標籤會顯示所選類型的所有物件所持有之參考類型的大小和數目。  
  
- 針對類型的選取實例，參考的**物件**會顯示所選實例所持有的物件。 您可以將滑鼠指標停留在名稱上，以在資料提示中檢視其資料值。  
  
  **迴圈參考**  
  
  第一個物件可參考第二個物件，而第二個物件對第一個物件有直接或間接參考。 當記憶體分析器遇到這種情況時，它會停止展開參考路徑，並將 **[偵測到迴圈]** 注釋加入至第一個物件的清單，並停止。  
  
  **根類型**  
  
  記憶體分析器會將註釋加入至根物件，以描述持有的參考類型：  
  
|Annotation|描述|  
|----------------|-----------------|  
|**靜態變數**`VariableName`|靜態變數。 `VariableName` 是變數的名稱。|  
|**最終控制碼**|完成項佇列中的參考|  
|**區域變數**|區域變數。|  
|**強式控制碼**|物件控制代碼資料表中的強式參考控制代碼。|  
|**Async.釘選的控制碼**|物件控制代碼資料表中的非同步固定物件。|  
|**相依控制碼**|物件控制代碼資料表中的相依物件。|  
|**釘選的控制碼**|物件控制代碼資料表中的固定強式參考。|  
|**RefCount 控制碼**|物件控制代碼資料表中的參考計數物件。|  
|**SizedRef 控制碼**|強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。|  
|**釘選的區域變數**|固定的區域變數。|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a>比較兩個記憶體快照集  
 您可以比較一個處理序的兩個傾印檔案，以找出可能造成記憶體流失的物件。 收集第一個 (較早的) 檔案到收集第二個 (較晚的) 檔案的間隔應該夠長，才能輕鬆看出造成記憶體流失之物件數目的成長量。 若要比較兩個檔案：  
  
1. 開啟第二個傾印檔案，然後選擇 [小型傾印檔案**摘要**] 頁面上的 [**調試 Managed 記憶體**]。  
  
2. 在 [記憶體分析報表] 頁面上，開啟 [**選取基準**] 清單，然後選擇 [**流覽]** 以指定第一個傾印檔案。  
  
   分析器會在報表的上方窗格中加入資料行，以顯示這些類型的**計數**、**大小**和**內含大小**之間的差異與先前快照中的值之間的差異。  
  
   ![類型清單中的 Diff 資料行](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   [**參考計數差異**] 資料行也會加入至 [**根的路徑**] 資料表。  
  
   ![回到頁首](../debugger/media/pcs-backtotop.png "PCS_BackToTop")[內容](#BKMK_Contents)  
  
## <a name="see-also"></a>另請參閱  
 [VS ALM TFS Blog：使用 Visual Studio 2013 診斷生產環境中的 .Net 記憶體問題](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio 電視&#124;受控記憶體分析](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio 工具箱&#124;中的 Managed 記憶體分析 Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)