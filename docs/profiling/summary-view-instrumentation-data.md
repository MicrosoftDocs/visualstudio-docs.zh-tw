---
title: 摘要檢視 - 檢測資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 606ba5ebe7c485adb33fbcfa6884ad5e625d821e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35668357"
---
# <a name="summary-view---instrumentation-data"></a>摘要檢視 - 檢測資料
[摘要] 檢視顯示有關程式碼剖析執行時效能耗費最多資源的函式資訊。 如需包括通知連結和報表清單描述在內的詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## <a name="timeline-graph"></a>時間軸圖形  
 [摘要] 檢視的時間軸圖形會顯示已進行程式碼剖析的應用程式在程式碼剖析期間的處理器 (CPU) 使用率。 您可以使用時間軸圖形，將檢視篩選為選取的時間範圍。 如需詳細資訊，請參閱[如何：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。  
  
## <a name="hot-path"></a>最忙碌路徑  
 [最忙碌路徑] 顯示耗用最多時間的執行路徑。 您可以按一下函式來顯示該函式的 [函式詳細資料] 檢視。 若要顯示該函式的其他檢視，以滑鼠右鍵按一下函式，然後按一下清單中的檢視。  
  
 [最忙碌路徑] 的每個函式都包含下列資料︰  
  
|資料行|描述|  
|------------|-----------------|  
|**名稱**|函式的名稱。|  
|**功能內含耗用 (Elapsed Inclusive) 時間 %**|在程式碼剖析執行時，該函式花費在執行其函式主體和其所呼叫函式中程式碼的所有時間百分比。|  
|**功能專屬耗用 (Elapsed Exclusive) 時間 %**|在程式碼剖析執行時，該函式花費在執行其函式主體中程式碼的所有時間百分比。 不包括該函式所呼叫函式中所花費的時間。|  
  
## <a name="functions-with-most-individual-work"></a>含有最多個別工作的函式  
 這份函式清單列出耗用最多時間在執行函式主體中程式碼 (而不是其所呼叫函式中的程式碼) 的函式。  
  
 [含有最多個別工作的函式] 的每個函式都包含下列資料︰  
  
|資料行|描述|  
|------------|-----------------|  
|**名稱**|函式的名稱。|  
|**專有時間 %**|在程式碼剖析執行時，該函式花費在執行其函式主體中程式碼的所有時間百分比。 不包括該函式所呼叫函式中所花費的時間。|  
  
## <a name="see-also"></a>另請參閱  
 [摘要檢視 - 取樣資料](../profiling/summary-view-sampling-data.md)   
 [摘要檢視 - .NET 記憶體資料](../profiling/summary-view-dotnet-memory-data.md)