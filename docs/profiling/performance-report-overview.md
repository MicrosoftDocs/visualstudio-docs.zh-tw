---
title: 效能報告概觀 | Microsoft Docs
description: 在 Visual Studio Team System 開發版整合式開發環境的 [效能報告] 視窗中，查看程式碼剖析資料。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2e775c91759326407918befba3dd4bb52e19dd0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922273"
---
# <a name="performance-report-overview"></a>效能報表概觀
您可以在 Visual Studio Team System Development Edition 整合式開發環境 (IDE) 的 [效能報告] 視窗中檢視效能工作階段的程式碼剖析資料。 程式碼剖析資料儲存在 .vsp 和 .vsps 檔案中。 [報表檢視] 視窗可讓您檢視和分析應用程式效能問題。

> [!CAUTION]
> 程式碼剖析資料檔案包含機密資訊，例如電腦名稱、作業系統版本、檔案路徑、記憶體資訊和其他電腦設定資訊。 您應該在其原生中維持對資料散發的嚴格控制。*.vsp* 格式以及將它匯出至時。*csv* 或。*xml* 檔案。
>
> 如果在效能會話中收集事件追蹤資料，其他資訊可能會出現在事件追蹤記錄檔 ( 中。*etl*) 檔。 這項資訊包括您的網域和使用者名稱；因此，您應嚴格控管記錄檔的散發。

## <a name="performance-report-window"></a>效能報表視窗
 [效能報告] 視窗是用來檢視、管理及篩選效能資料的工具視窗，並包含可自訂的查詢控制項。

 您可以在 [效能報告] 視窗的主要工具列上存取每個檢視。 按一下 [目前檢視] 清單旁的箭號，以顯示和選取可用的個別檢視。

 [效能報告] 視窗提供下列資料檢視︰

### <a name="summary-view"></a>摘要檢視
 根據預設，程式碼剖析資料會顯示在 [摘要] 檢視中。 此檢視您調查效能問題的起點。 從 [摘要] 檢視的每一行，只要以滑鼠右鍵按一下函式或模組名稱，即可移至更詳細的檢視。 如需詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。

### <a name="callercallee-view"></a>呼叫端/被呼叫端檢視
 [呼叫者/被呼叫者] 檢視顯示個別函式的呼叫樹狀圖。 此檢視分為三個部分：

- 目標函式會顯示在檢視的中間。

- 呼叫該函式的函式 (呼叫者) 會顯示在目標函式上方。

- 目標函式呼叫的函式 (被呼叫者) 會顯示在目標下方。

  您可以按兩下呼叫的清單或被呼叫者清單來選取不同的函式。 如需詳細資訊，請參閱[呼叫者/被呼叫者檢視](../profiling/caller-callee-view.md)。

### <a name="call-tree-view"></a>呼叫樹狀圖檢閱
 [呼叫樹狀圖] 檢視顯示在分析的應用程式中周遊的函式執行路徑。 樹狀圖的根是應用程式或元件的進入點。 每個函式節點會列出它所呼叫的所有函式，以及這些函式呼叫的相關效能資料。

 [呼叫樹狀圖] 檢視也可展開並反白顯示花最多時間或最常取樣的函式的執行路徑。 若要顯示最常使用的路徑，請以滑鼠右鍵按一下函式，然後按一下 [展開最忙碌路徑]。 如需詳細資訊，請參閱[呼叫樹狀圖檢視](../profiling/call-tree-view.md)。

### <a name="process-view"></a>處理序檢視
 [處理序] 檢視顯示已剖析的每個處理序和執行緒的效能資料。 如需詳細資訊，請參閱[處理序檢視](../profiling/process-view.md)。

### <a name="modules-view"></a>模組檢視
 [模組] 檢視列出專案中的模組，並顯示每個模組的程式碼剖析資料。 展開或摺疊模組名稱來顯示函式程式碼剖析資料。 當資料是以取樣方式收集時，也會提供原始程式碼行和指令指標程式碼剖析資料。 如需詳細資訊，請參閱[模組檢視](../profiling/modules-view.md)。

### <a name="functions-view"></a>函式檢視
 [函式] 檢視列出程式碼剖析期間呼叫的函式。 如需詳細資訊，請參閱[函式檢視](../profiling/functions-view.md)。

### <a name="line-view"></a>程式行檢視
 [程式行] 檢視可讓您檢視取樣程式碼剖析期間所執行的特定原始程式碼行。 如需詳細資訊，請參閱 [線條視圖](../profiling/lines-view.md)。

### <a name="instruction-pointer-ip-view"></a>指令指標 (IP) 檢視
 [指令指標] 檢視可讓您檢視取樣程式碼剖析期間所執行的特定指標。 如需詳細資訊，請參閱[指令指標 (IP) 檢視](../profiling/instruction-pointers-ips-view.md)。

### <a name="allocation-view"></a>配置檢視
 如果在 [效能工作階段] 屬性對話方塊的 [一般] 頁面上選取 [收集 .NET 物件配置]，則會顯示 [配置] 檢視。 請參閱[效能工作階段概觀](../profiling/performance-session-overview.md)。 [配置] 檢視列出應用程式或元件所配置的 .NET 物件。 展開物件資料列時，會顯示呼叫樹狀圖。 呼叫樹狀圖會顯示導致物件建立的執行路徑。 也會顯示有關呼叫樹狀圖中每個函式的內含和專有配置數目的資訊。 [配置] 檢視也可展開並反白顯示配置最大物件數目的函式的執行路徑。 若要顯示最常使用的路徑，請以滑鼠右鍵按一下函式，然後按一下 [展開最忙碌路徑]。 如需詳細資訊，請參閱[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)和[配置檢視](../profiling/dotnet-memory-allocations-view.md)。

### <a name="objects-lifetime-view"></a>物件存留期檢視
 如果在 [效能工作階段] 屬性對話方塊的 [一般] 頁面上選取 [收集 .NET 物件配置資訊] 和 [同時收集 .NET 物件存留期的資訊]，則會顯示 [物件存留期] 檢視。

 [物件存留期] 檢視顯示每個型別的執行個體總數和每個記憶體回收層代中所收集的物件數目。 如需詳細資訊，請參閱[物件存留期檢視](../profiling/object-lifetime-view.md)。

## <a name="customizable-filter-control"></a>可自訂的篩選控制項
 可自訂的篩選控制項具有下列選項︰

- **匯入篩選** - 擷取先前儲存的自訂查詢。

- **匯出篩選** - 將自訂查詢儲存至指定的位置。

- **執行查詢** - 執行自訂查詢控制項中顯示的查詢。

- **停止查詢** - 停止執行正在執行的查詢。 如果沒有查詢正在執行，則不會顯示此按鈕。

- **顯示查詢** - 顯示或隱藏自訂查詢控制項。

-  - 將報告連同其目前的分析儲存成 .vsps 檔案。

- **匯出** - 將目前的報告儲存在 .CVS 格式或 .XML 格式檔案，提供選項以儲存不同的檢視。

## <a name="see-also"></a>另請參閱
- [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)
- [效能報表檢視](../profiling/performance-report-views.md)
