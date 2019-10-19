---
title: PROFILER_EVENT_MASK 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572290"
---
# <a name="profiler_event_mask-enumeration"></a>PROFILER_EVENT_MASK 列舉
表示應該分析的事件種類。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|設定檔函式，定義于使用者撰寫的腳本和動態程式碼中。|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|分析腳本引擎所定義的原生函式。|  
|PROFILER_EVENT_MASK_TRACE_ALL|分析所有使用者定義和腳本引擎函式，但不包括呼叫檔物件模型（DOM）。|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|呼叫 DOM 的設定檔函數。|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|分析所有函式，包括對 DOM 的呼叫。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl：： SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)    
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)