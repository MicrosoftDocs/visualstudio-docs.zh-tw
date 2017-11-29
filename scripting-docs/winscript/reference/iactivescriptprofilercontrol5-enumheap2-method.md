---
title: "Iactivescriptprofilercontrol5:: Enumheap2 方法 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 方法
傳回的介面 ([IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md))，可用來逐一查看 GC 堆積中物件的內容相關聯的指令碼引擎。  
  
 您可以呼叫這個方法在其中一個偵錯或發行模式。 UI 執行緒處於閒置狀態時，應該呼叫這個方法。 在呼叫方法之後，應該執行任何作業指令碼引擎，除了針對[iactivescriptprofilerheapenum:: Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)直到[iactivescriptprofilerheapenum:: Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)返回 S_FALSE 或[IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)釋放介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>參數  
 enumFlags  
 值，指定是否要公開指向物件關聯性中之物件的相關額外資訊。 額外的資訊可能指向的物件是否為 getter 或 setter 方法來表示。 如需詳細資訊，請參閱[PROFILER_HEAP_ENUM_FLAGS 列舉](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)。  
  
 ppEnum  
 [out]傳回[IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|堆積列舉型別已順利完成。|  
|`E_OUTOFMEMORY`|沒有記憶體不足，無法執行堆積列舉型別。|  
|`E_FAIL`|發生內部錯誤。|