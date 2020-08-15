---
title: 瞭解效能收集方法 |Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecbabae86b762c9143dba6be5aa0e4683a92b0dd
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250771"
---
# <a name="understand-performance-collection-methods"></a>了解效能收集方法

Visual Studio 程式碼剖析工具提供五種收集效能資料的方法。 本文說明不同的方法，並建議使用特定方法收集資料的案例可能是適當的。

> [!NOTE]
> Windows 8 和 Windows Server 2012 中增強的安全性功能需要在 Visual Studio profiler 收集這些平臺資料的方式上有重大變更。 UWP App 也需要新的收集技術。 請參閱 [windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

|方法|描述|
|------------|-----------------|
|[取樣](#sampling)|收集應用程式所完成之工作的相關統計資料。|
|[校驗](#instrumentation)|收集有關每個函式呼叫的詳細計時資訊。|
|[並行](#concurrency)|收集多執行緒應用程式的詳細資訊。|
|[.NET 記憶體](#net-memory)|收集有關 .NET 記憶體配置和記憶體回收的詳細資訊。|
|[階層互動](#tier-interaction)|收集 SQL Server 資料庫之同步 ADO.NET 函式呼叫的相關資訊。<br /><br /> 任何版本的 Visual Studio 都可以收集層互動設定檔資料。 不過，您只能在 Visual Studio Enterprise 中查看該資料。|

藉由使用一些分析方法，您也可以收集其他資料，例如軟體和硬體效能計數器。 如需詳細資訊，請參閱[收集其他效能資料](../profiling/collecting-additional-performance-data.md)。

## <a name="sampling"></a>取樣

取樣分析方法會收集應用程式在分析執行期間所執行之工作的相關統計資料。 取樣方法非常輕量，而且對應用程式方法的執行沒有太大的影響。

取樣是 Visual Studio 程式碼剖析工具的預設方法。 這適用于下列工作：

- 應用程式效能的初始探勘
- 調查牽涉到微處理器 (CPU 使用率的效能問題) 

取樣分析方法會依設定的間隔來中斷電腦 CPU，並收集函式呼叫堆疊。 執行之函式的專屬樣本計數會遞增。 「內含計數」會針對呼叫堆疊上的所有呼叫函式遞增。 取樣報表會針對已分析的模組、函式、源程式碼及指示，呈現這些計數的總計。

根據預設，分析工具會將取樣間隔設定為 CPU 週期。 您可以將 [間隔類型] 變更為另一個 CPU 效能計數器，或設定間隔的計數器事件數目。 您也可以 (TIP) 資料收集階層互動分析。 此資料會提供透過 ADO.NET 對 SQL Server 資料庫進行查詢的相關資訊。

[使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)

[了解取樣資料值](../profiling/understanding-sampling-data-values.md)

[取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>測試設備

檢測分析方法會收集分析應用程式中函式呼叫的詳細時機。 檢測分析適用于下列工作：

- 調查輸入/輸出瓶頸，例如磁片 i/o
- 關閉特定模組或函數集的檢查

檢測方法會將程式碼插入二進位檔案中。 此程式碼會針對檢測檔案中的所有函式，以及這些函式所做的每個函式呼叫，捕捉計時資訊。 檢測也會識別函數針對寫入檔案等作業呼叫作業系統的時間。

檢測報表會使用這四個值來代表在函式或源程式碼中花費的總時間：

- 功能內含-執行函式或源程式碼所花費的總時間。

- 應用程式內含-執行函式或源程式碼所花費的時間。 系統會排除對作業系統的呼叫。

- 功能專屬-執行函式或源程式碼所花費的時間。 已排除對其他函式的呼叫。

- 應用程式獨佔-執行函式或源程式碼所花費的時間。 作業系統或其他函式的呼叫會被排除。

您也可以使用檢測方法來收集 CPU 和軟體效能計數器。

[了解檢測資料值](../profiling/understanding-instrumentation-data-values.md)

[使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>並行

並行分析會收集多執行緒應用程式的相關資訊。 資源爭用分析會在每次競爭執行緒等候共用資源的存取權時，收集詳細的呼叫堆疊資訊。 並行視覺化也會收集有關多執行緒應用程式如何互動的一般資訊：

- 直接.
- 硬體。
- 作業系統。
- 主機電腦上的其他進程。

資源爭用報表會顯示爭用總數。 他們也會回報模組、函式、源程式碼和指示等候資源的總時間。 時間軸圖形會顯示其發生的爭用。

並行視覺化會顯示圖形資訊，協助您找出：

- 效能瓶頸。
- CPU 使用量過低。
- 執行緒爭用。
- 執行緒遷移。
- 同步處理延遲。
- 重迭的 i/o 區域。

  可能的話，圖形輸出會從呼叫堆疊和原始程式碼連結到資料。 並行視覺化資料只能針對命令列應用程式和 Windows 應用程式收集。

[了解資源爭用資料值](../profiling/understanding-resource-contention-data-values.md)

[收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)

[資源爭用資料檢視](../profiling/resource-contention-data-views.md)

[並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET 記憶體

.NET 記憶體配置的分析方法會中斷分析應用程式中每個 .NET Framework 物件配置的 CPU。 當分析工具也會收集物件存留期資料時，它會在每次 .NET Framework 垃圾收集之後中斷 CPU。

分析工具會收集在配置中建立或在垃圾收集時損毀之物件的類型、大小和數目相關資訊。

- 發生配置事件時，分析工具會收集有關函式呼叫堆疊的其他資訊。 分析工具會針對目前正在執行的函式遞增獨佔配置計數。 它也會遞增呼叫堆疊上所有呼叫函式的內含計數。 .NET 報表會針對已分析的類型、模組、函式、源程式碼及指示，呈現這些計數的總計。

- 當垃圾收集發生時，分析工具會收集有關已終結物件的資料，以及每個垃圾收集產生中物件的相關資訊。 在程式碼剖析執行結束時，分析工具會記錄未明確終結之物件的相關資料。 物件存留期報表會顯示在程式碼剖析執行中配置的每個類型的總計。

您可以在取樣模式或檢測模式中使用 .NET 記憶體分析。 您選取的模式不會影響 .NET 記憶體分析特有的配置和物件存留期報表。

- 當您在取樣模式中執行 .NET 記憶體分析時，profiler 會使用記憶體配置事件做為間隔。 它也會顯示配置的物件總數和位元組數，做為報表中的內含和排除值。

- 當您在檢測模式中執行 .NET 記憶體分析時，程式碼剖析工具會收集詳細的計時資訊，以及內含和專有配置值。

[瞭解記憶體配置和物件存留期資料值](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>階層互動

階層互動分析會將有關 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面或其他應用程式與資料庫之間同步呼叫的資訊新增至程式碼剖析資料檔案 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 。 資料包括呼叫的數目和時間，以及最大和最短的時間。 您可以將階層互動資料新增至您使用取樣、檢測、.NET 記憶體或並行方法收集的分析資料。

![層互動分析資料流](../profiling/media/tierinteraction_profilingtools.png "層互動分析資料流")

如需分析工具所收集之階層互動資料的詳細資訊，請參閱下列文章。

[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)

[層互動視圖](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>另請參閱

[如何：收集網站的效能資料](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[效能分析的初學者指南](../profiling/beginners-guide-to-performance-profiling.md)
