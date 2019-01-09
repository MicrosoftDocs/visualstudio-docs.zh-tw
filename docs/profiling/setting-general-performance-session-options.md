---
title: 設定一般效能工作階段選項 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3dce2f53ef0e16563ff73d188e5d475c42bf0fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896405"
---
# <a name="set-general-performance-session-options"></a>設定一般效能工作階段選項

您可以在效能工作階段屬性對話方塊的 [一般] 頁面上設定 Visual Studio 分析工具效能工作階段的收集方法和分析資料命名慣例。 若要從 [效能總管] 中開啟此對話方塊，請以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性]。

## <a name="choosing-data-collection-methods"></a>選擇資料收集方法

您可以選取 [分析集合] 下的其中一個選項來設定基底收集方法。 下表描述這些選項：

|||
|-|-|
|**取樣**。 取樣方法會依固定間隔收集分析資訊。 此方法可用來尋找處理器使用率問題，建議用來調查大多數效能問題。|- [使用取樣收集效能統計資料](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**檢測**。 檢測方法會插入至模組分析程式碼的複本，以記錄分析回合期間模組中函式的每個進入、結束和函式呼叫。 此方法可用來收集程式碼區段的詳細計時資訊，以及了解輸入和輸出作業對應用程式效能的影響。|- [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**並行**。 並行方法會收集每個封鎖執行程式碼之事件的資料，例如，執行緒等待釋放鎖定應用程式資源存取時。 此方法適用於分析多執行緒應用程式。|- [收集執行緒和處理序並行資料](../profiling/collecting-thread-and-process-concurrency-data.md)|

 您可以使用取樣或檢測方法來收集 .NET 記憶體資料。 您可以在 [.NET 記憶體分析] 下選取資料類型。

|||
|-|-|
|**收集 .NET 物件配置資訊**. 根據預設，資料會包含已配置的物件數目和大小。 選取或清除此核取方塊，以啟用或停用 .NET 記憶體資料收集。 |- [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**同時收集 .NET 物件存留期的資訊**. 選取此核取方塊，以包含用來回收記憶體物件之記憶體回收世代的資料。|- [收集 .NET 記憶體配置和存留期資料](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 當您開始對應用程式進行程式碼剖析時，程式碼剖析工作階段頁面就會出現，您可以在此暫停、繼續執行及停止程式碼剖析。

 ![程式碼剖析工作階段頁面](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>設定分析資料檔案選項

|||
|-|-|
|**報表**。 根據預設，分析資料 (.vsp) 檔案會得到所分析應用程式的名稱，並位在方案或專案資料夾中。 日期字串也會附加到名稱，而且遞增的數字會新增至資料檔案，因此名稱不會重複。 您可以變更這些選項。|- [如何：設定效能資料檔案名稱選項](../profiling/how-to-set-performance-data-file-name-options.md)|