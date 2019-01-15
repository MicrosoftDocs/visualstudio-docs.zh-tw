---
title: 摘要檢視 - 取樣資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0b1c1da6bd493fc53419ef5b371b74488002e27
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938601"
---
# <a name="summary-view---sampling-data"></a>摘要檢視 - 取樣資料
[摘要] 檢視顯示有關程式碼剖析執行時效能耗費最多資源的函式資訊。 如需包括通知連結和報表清單描述在內的詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## <a name="timeline-graph"></a>時間軸圖形  
 [摘要] 檢視的時間軸圖形會顯示已進行程式碼剖析的應用程式在程式碼剖析期間的處理器 (CPU) 使用率百分比。 您可以使用時間軸圖形，將檢視篩選為選取的時間範圍。 如需詳細資訊，請參閱[＜How to：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。  
  
## <a name="hot-path"></a>最忙碌路徑  
 「最忙碌路徑」顯示收集到最多樣本的執行路徑。 您可以按一下函式來顯示該函式的 [函式詳細資料] 檢視。 若要顯示該函式的其他檢視，以滑鼠右鍵按一下函式，然後按一下清單中的檢視。  
  
 [最忙碌路徑] 的每個函式都包含下列資料︰  
  
|資料行|說明|  
|------------|-----------------|  
|**名稱**|函式的名稱。|  
|**內含樣本 %**|此函式或由此函式呼叫的函式執行時發生的所有樣本百分比。|  
|**專有樣本 %**|函式在執行其函式主體中的程式碼時發生的所有樣本百分比。 不包含在此函式所呼叫的函式中收集到的樣本。|  
  
## <a name="functions-doing-most-individual-work"></a>執行最多個別工作的函式  
 [執行最多個別工作的函式] 清單會顯示在程式碼剖析執行時具有最多專有樣本數的函式。 如果收集到樣本時，函式正在執行自己的程式碼，便會將專有樣本指派給該函數。 如果收集到樣本時，函式正在呼叫另一個函式，則不會將專有樣本指派給該函數。 有大量專有樣本表示花費很長時間在該函式本身。  
  
 您可以按一下函式來顯示該函式的 [函式詳細資料] 檢視。 若要顯示該函式的其他檢視，以滑鼠右鍵按一下函式，然後按一下清單中的檢視。  
  
 [執行最多個別工作的函式] 的每個函式都包含下列資料︰  
  
|資料行|說明|  
|------------|-----------------|  
|**名稱**|函式的名稱。|  
|**專有樣本 %**|當函式正在執行其函式主體中的程式碼時，在程式碼剖析執行時收集到的所有樣本百分比。 不包括此函式所呼叫的函式正在執行時所收集到的樣本百分比。|  
  
## <a name="see-also"></a>另請參閱  
 [摘要檢視 - .NET 記憶體資料](../profiling/summary-view-dotnet-memory-data.md)   
 [摘要檢視 - 檢測資料](../profiling/summary-view-instrumentation-data.md)