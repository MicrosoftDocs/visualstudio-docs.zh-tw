---
title: 瞭解效能收集方法 |Microsoft Docs
description: 瞭解使用特定方法收集資料可能適用的不同案例。
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8126d2331e126cf9162a0334b59be239684754c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886089"
---
# <a name="understand-performance-collection-methods"></a>了解效能收集方法

Visual Studio 程式碼剖析工具提供五種方法來收集效能資料。 本文說明不同的方法，並建議使用特定方法收集資料的情況可能會很適當。

> [!NOTE]
> Windows 8 和 Windows Server 2012 中的增強式安全性功能，需要在 Visual Studio profiler 如何在這些平臺上收集資料的重大變更。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

|方法|描述|
|------------|-----------------|
|[取樣](#sampling)|收集應用程式完成之工作的相關統計資料。|
|[儀錶](#instrumentation)|收集有關每個函式呼叫的詳細計時資訊。|
|[並行](#concurrency)|收集多執行緒應用程式的詳細資訊。|
|[.NET 記憶體](#net-memory)|收集有關 .NET 記憶體配置和記憶體回收的詳細資訊。|
|[階層互動](#tier-interaction)|收集 SQL Server 資料庫同步 ADO.NET 函式呼叫的相關資訊。<br /><br /> 任何版本的 Visual Studio 都可以收集階層互動設定檔資料。 不過，您只能在 Visual Studio Enterprise 中看到該資料。|

藉由使用某些分析方法，您也可以收集其他資料，例如軟體和硬體效能計數器。 如需詳細資訊，請參閱[收集其他效能資料](../profiling/collecting-additional-performance-data.md)。

## <a name="sampling"></a>取樣

取樣分析方法會收集應用程式在執行程式碼剖析期間所執行之工作的相關統計資料。 取樣方法是輕量的，對應用程式方法的執行不會有太大的影響。

取樣是 Visual Studio 程式碼剖析工具的預設方法。 適用于下列工作：

- 應用程式效能的初始探勘
- 調查涉及 CPU (CPU 使用率的效能問題) 

取樣分析方法會依設定的間隔來中斷電腦 CPU，並收集函式呼叫堆疊。 針對正在執行的函式，其專有樣本計數會遞增。 呼叫堆疊上所有呼叫函式的內含計數會遞增。 取樣報表會針對已分析的模組、函式、源程式碼及指示，顯示這些計數的總計。

根據預設，分析工具會將取樣間隔設定為 CPU 週期。 您可以將間隔類型變更為另一個 CPU 效能計數器，或設定間隔的計數器事件數目。 您也可以收集階層互動分析 (提示) 資料。 此資料會提供透過 ADO.NET 對 SQL Server 資料庫進行查詢的相關資訊。

[使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)

[了解取樣資料值](../profiling/understanding-sampling-data-values.md)

[取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>測試設備

檢測分析方法會收集分析應用程式中函式呼叫的詳細時間。 檢測分析適用于下列工作：

- 調查輸入/輸出瓶頸，例如磁片 i/o
- 關閉特定模組或一組函數的檢查

檢測方法會將程式碼插入二進位檔案中。 此程式碼會捕獲檢測檔案中所有函式的計時資訊，以及這些函式所進行的每個函式呼叫。 檢測也會識別函式呼叫作業系統中是否有寫入檔案等作業。

檢測報表會使用這四個值來代表在函式或源程式碼中花費的總時間：

- 功能內含-執行函式或源程式碼所花費的總時間。

- 應用程式內含-執行函式或源程式碼所花費的時間。 系統會排除對作業系統的呼叫。

- 經過的獨佔-執行函式或源程式碼所花費的時間。 其他函式的呼叫會被排除。

- 應用程式專屬-執行函式或源程式碼所花費的時間。 系統會排除對作業系統或其他函式的呼叫。

您也可以使用檢測方法來收集 CPU 和軟體效能計數器。

[了解檢測資料值](../profiling/understanding-instrumentation-data-values.md)

[使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>並行

並行分析會收集多執行緒應用程式的相關資訊。 資源爭用分析會在每次有競爭執行緒等候共用資源的存取權時，收集詳細的呼叫堆疊資訊。 平行存取視覺效果也會收集有關多執行緒應用程式如何與互動的一般資訊：

- 本身。
- 硬體。
- 作業系統。
- 主機電腦上的其他進程。

資源爭用報表會顯示爭用總數。 它們也會報告模組、函式、源程式碼及指示等候資源的總時間。 時間軸圖形會顯示發生的爭用。

並行視覺化顯示可協助您找到的圖形資訊：

- 效能瓶頸。
- CPU 使用量過低。
- 執行緒爭用。
- 執行緒遷移。
- 同步處理延遲。
- 重迭 i/o 的區域。

  可能的話，圖形化輸出會連結至來自呼叫堆疊和原始程式碼的資料。 您只能針對命令列應用程式和 Windows 應用程式收集平行存取視覺效果資料。

[了解資源爭用資料值](../profiling/understanding-resource-contention-data-values.md)

[收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)

[資源爭用資料檢視](../profiling/resource-contention-data-views.md)

[並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET 記憶體

.NET 記憶體配置的程式碼剖析方法會在程式碼剖析的應用程式中 .NET Framework 物件的每個配置時，中斷 CPU。 當分析工具也收集物件存留期資料時，它會在每次 .NET Framework 垃圾收集之後中斷 CPU。

分析工具會收集在配置中建立或在垃圾收集中損毀之類型、大小和物件數目的相關資訊。

- 發生配置事件時，分析工具會收集有關函式呼叫堆疊的其他資訊。 分析工具會遞增目前正在執行之函式的獨佔配置計數。 它也會遞增呼叫堆疊上所有呼叫函式的內含計數。 .NET 報表會針對已分析的類型、模組、函式、源程式碼和指示，顯示這些計數的總計。

- 當垃圾收集發生時，分析工具會收集有關已終結物件的資料，以及每個垃圾收集產生中的物件。 在分析執行結束時，分析工具會記錄未明確終結之物件的相關資料。 [物件存留期] 報表會顯示分析回合中所配置之每個類型的總計。

您可以使用取樣模式或檢測模式來使用 .NET 記憶體程式碼剖析。 您選取的模式不會影響 .NET 記憶體分析特有的配置和物件存留期報表。

- 當您在取樣模式中執行 .NET 記憶體分析時，分析工具會使用記憶體配置事件做為間隔。 它也會顯示已配置的物件數目和位元組總數，以作為報表中的內含和專有值。

- 當您在檢測模式中執行 .NET 記憶體分析時，分析工具會收集詳細的時間資訊以及內含和專屬配置值。

[瞭解記憶體配置和物件存留期資料值](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>階層互動

階層互動分析會將資訊新增至 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 頁面或其他應用程式與資料庫之間的同步呼叫相關的分析資料檔 [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 。 資料包含通話的數目和時間，以及最大和最小時間。 您可以將階層互動資料新增至使用取樣、檢測、.NET 記憶體或並行方法所收集的分析資料。

![階層互動分析資料流](../profiling/media/tierinteraction_profilingtools.png "階層互動分析資料流")

如需分析工具所收集之階層互動資料的詳細資訊，請參閱下列文章。

[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)

[層互動視圖](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>另請參閱

[如何：收集網站的效能資料](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[效能分析的初學者指南](../profiling/beginners-guide-to-performance-profiling.md)
