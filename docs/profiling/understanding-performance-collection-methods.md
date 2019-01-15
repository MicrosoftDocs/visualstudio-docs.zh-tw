---
title: 了解效能收集方法 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bde4e313b9baf4975f5bff247fac248f3a090ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825785"
---
# <a name="understand-performance-collection-methods"></a>了解效能收集方法

Visual Studio 程式碼剖析工具提供五種方法讓您收集效能資料。 本主題說明不同方法，並建議一些適合利用特定方法收集資料的案例。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

|方法|說明|
|------------|-----------------|
|[取樣](#sampling)|收集應用程式所執行的工作相關統計資料。|
|[檢測](#instrumentation)|收集有關每個函式呼叫的詳細計時資訊。|
|[並行](#concurrency)|收集有關多執行緒應用程式的詳細資訊。|
|[.NET 記憶體](#net-memory)|收集有關 .NET 記憶體配置和記憶體回收的詳細資訊。|
|[階層互動](#tier-interaction)|收集 SqlServer 資料庫的同步 ADO.NET 函式呼叫相關資訊。<br /><br /> 階層互動分析可以使用任何版本的 Visual Studio 來收集。 不過，階層互動分析資料只能在 Visual Studio Enterprise 中檢視。|

藉由使用某些分析方法，您也可以收集其他資料，例如軟體和硬體的效能計數器。 如需詳細資訊，請參閱[收集其他效能資料](../profiling/collecting-additional-performance-data.md)。

## <a name="sampling"></a>取樣

取樣分析方法可收集應用程式在執行程式碼剖析期間所執行工作的相關統計資料。 取樣方法屬於輕量型，對於執行應用程式方法影響並不大。

取樣是 Visual Studio 程式碼剖析工具的預設方法。 適用於下列項目︰

- 初始瀏覽應用程式的效能。
- 調查有關處理器 (CPU) 使用率的效能問題。

取樣分析方法會依設定的間隔來中斷電腦處理器，並收集函式呼叫堆疊。 專有樣本計數會隨執行的函式而遞增，而內含計數會隨呼叫堆疊上所有呼叫的函式而遞增。 取樣報表會呈現已進行程式碼剖析的模組、函式、原始程式碼行及指示這些計數的總計。

根據預設，分析工具會將取樣間隔設定為 CPU 週期。 您可以將間隔類型變更為另一個 CPU 效能計數器，並可設定間隔的計數器事件數目。 您也可以收集階層互動分析 (TIP) 資料，透過 ADO.NET 提供對 SQL 伺服器資料庫所做的查詢相關資訊。

[使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)

[認識取樣資料值](../profiling/understanding-sampling-data-values.md)

[取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>測試設備

檢測分析方法可收集已進行程式碼剖析的應用程式中詳細的函式呼叫計時資料。 檢測分析適用於下列項目：

- 調查輸入/輸出瓶頸，例如磁碟 I/O。
- 關閉特定模組或一組函式的檢查。

檢測方法會將程式碼插入至二進位檔，擷取已檢測檔案中每個函式的計時資訊，以及那些函式所發出的每個函式呼叫。 檢測也可指出函式呼叫何時進入像是寫入至檔案的作業。 檢測報表會使用四個值來表示函式或原始程式碼行所花費的時間總計︰

- 功能內含耗用 (Elapsed Inclusive) - 花費在執行函式或原始程式碼的時間總計。

- 應用程式內含 (Application Inclusive) - 花費在執行函式或原始程式碼的時間，但不包括花費在呼叫作業系統的時間。

- 功能專屬耗用 (Elapsed Exclusive) - 花費在執行函式或原始程式碼行主體的時間。 不包括花費在執行函式或原始程式碼所取消函式的時間。

- 應用程式專屬 (Elapsed Exclusive) - 花費在執行函式或原始程式碼行主體的時間。 花費在呼叫作業系統的執行時間，但不包括花費在執行函式或原始程式碼所取消函式的時間。

您也可以使用檢測方法，收集 CPU 和軟體效能計數器。

[了解檢測資料值](../profiling/understanding-instrumentation-data-values.md)

[使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>並行

並行程式碼剖析會收集有關多執行緒應用程式的資訊。 資源爭用分析會在每次強迫競爭執行緒等候共用資源的存取權時，收集詳細的呼叫堆疊資訊。 並行視覺化也會收集有關多執行緒應用程式如何與其本身、硬體、作業系統及主機電腦上的其他處理序互動的一般詳細資訊：

- 資源爭用報表可顯示爭用總數，以及等候資源以用於發生等候的模組、函式、原始碼程式行及指示所花費的總時間。 時間軸圖表也會顯示發生的爭用情況。

- 並行視覺化檢視顯示的圖形化資訊可讓您用來找出效能瓶頸、CPU 使用率不彰、執行緒爭用、執行緒移轉、同步處理延遲、I/O 重疊區域以及其他資訊。 請盡可能將圖形化輸出連結至呼叫堆疊和原始程式碼資料。 只會針對命令列和 Windows 應用程式來收集並行視覺化資料。

[了解資源爭用資料值](../profiling/understanding-resource-contention-data-values.md)

[收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)

[資源爭用資料檢視](../profiling/resource-contention-data-views.md)

[並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET 記憶體

.NET 記憶體配置分析方法會在每次於已進行程式碼剖析的應用程式中配置 .NET Framework 物件時，中斷電腦處理器。 也會收集物件存留期資料時，分析工具會在每次 .NET Framework 記憶體回收之後中斷處理器。

分析工具會收集有關配置時建立或在記憶體回收時終結的類型、大小及物件數目資訊。

- 發生配置事件時，分析工具會收集有關函式呼叫堆疊的其他資訊。 專有配置計數會隨目前執行的函式而遞增，而內含計數會隨呼叫堆疊上所有呼叫的函式而遞增。 .NET 報表會呈現已進行程式碼剖析的類型、模組、函式、原始程式碼行及指示這些計數的總計。

- 發生記憶體回收時，分析工具會在每一記憶體回收層代收集有關已終結物件的資料以及物件的相關資訊。 在程式碼剖析執行結束時，分析工具會記錄有關未明確終結的物件資料。 物件存留期報表會顯示在執行程式碼剖析期間配置的各種類型總計。

.NET 記憶體分析可用於取樣或檢測模式。 您選取的模式不會影響 .NET 記憶體分析特有的配置和物件存留期報表：

- 當您在取樣模式中執行.NET 記憶體分析時，分析工具 .NET 會使用記憶體配置事件做為間隔，並顯示在報表中配置為內含和專有值的總位元組數。

- 當您在檢測模式中執行.NET 記憶體分析時，會收集詳細的計時資訊以及內含與專有配置值。

[了解記憶體配置和物件存留期資料值](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>階層互動

階層互動分析會將有關 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面或其他應用程式與 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫之間的同步 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 呼叫資訊，加入至程式碼剖析資料檔案。 資料包括呼叫的數目和時間，以及最大和最小次數。 階層互動資料可以加入至利用取樣、檢測、.NET 記憶體或並行方法收集的分析資料。

![階層互動分析資料](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")

由程式碼剖析工具收集的階層互動資料

[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)

[階層互動檢視](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>另請參閱

[如何：收集網站的效能資料](../profiling/how-to-collect-performance-data-for-a-web-site.md)  
[效能分析的初學者指南](../profiling/beginners-guide-to-performance-profiling.md)