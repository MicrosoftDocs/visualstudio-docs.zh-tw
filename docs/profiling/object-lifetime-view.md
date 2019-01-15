---
title: 物件存留期檢視 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8175a8337f15517e0b9c88ae3f5405148a4b22b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934965"
---
# <a name="object-lifetime-view"></a>物件存留期檢視
在 [效能工作階段] 屬性頁上核取 [同時收集 .NET 物件存留期的資料] 時，可以使用 [物件存留期] 檢視。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的記憶體回收行程可管理應用程式的記憶體配置和釋放。 為了要最佳化記憶體回收行程的效能，受控堆積分成三個世代：0、1 和 2。 執行階段的記憶體回收行程會將新的物件儲存至世代 0。 在回收之後存留下來的物件則會升階並儲存在層代 1 與 2。  
  
 記憶體回收行程會取消配置整個物件層代來回收記憶體。 對於已分析的應用程式所建立的物件，[物件存留期] 檢視會顯示物件的數目和大小，以及回收時的世代。  
  
## <a name="general"></a>一般  
  
|資料行|說明|  
|------------|-----------------|  
|**類別名稱**|已配置類型的類別名稱。|  
|**處理序 ID**|分析執行的處理序 ID。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
  
## <a name="instance-data"></a>執行個體資料  
 執行個體資料指出分析回合中所建立類型的物件數目，以及記憶體回收行程所解除配置物件的世代。  
  
|資料行|說明|  
|------------|-----------------|  
|**執行個體**|這類型之物件的配置數目。|  
|**總執行個體 %**|分析回合中進行的配置總數百分比。|  
|**Gen 0 執行個體已收集**|已在記憶體回收演算法世代 0 解除配置之類型的執行個體數目。|  
|**Gen 1 執行個體已收集**|已在記憶體回收演算法世代 1 解除配置之類型的執行個體數目。|  
|**Gen 2 執行個體已收集**|已在記憶體回收演算法世代 2 解除配置之類型的執行個體數目。|  
|**現存的執行個體**|在分析回合結束之前未解除配置之類型的執行個體數目。|  
  
## <a name="size-byte-data"></a>大小 (位元組) 資料  
 大小 (位元組) 資料指出分析回合中所建立類型的物件大小，以及在每個解除配置物件的世代中所回收的記憶體數量。  
  
|資料行|說明|  
|------------|-----------------|  
|**配置的總位元組數**|類型之所有執行個體的位元組總數。|  
|**總位元組 %**|分析回合中配置給此類型執行個體的已配置位元組總數百分比。|  
|**Gen 0 位元組已收集**|已在記憶體回收演算法世代 0 解除配置之類型的執行個體大小。|  
|**Gen 1 位元組已收集**|已在記憶體回收演算法世代 1 解除配置之類型的執行個體大小。|  
|**Gen 2 位元組已收集**|已在記憶體回收演算法世代 2 解除配置之類型的執行個體大小。|  
  
## <a name="large-object-heap-data"></a>大型物件堆積資料  
 .NET 記憶體配置器可管理與標準 Managed 堆積不同的位置中的超大型物件。 大型物件堆積資料指出在此位置管理之類型的物件數目和大小。  
  
|資料行|說明|  
|------------|-----------------|  
|**大型物件堆積執行個體已收集**|位於大型物件堆積以及在分析回合中所收集之此類型的執行個體數目。|  
|**大型物件堆積位元組已收集**|位於大型物件堆積以及在分析回合中所收集之此類型的執行個體大小 (以位元組為單位)。|  
  
## <a name="see-also"></a>另請參閱  
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)