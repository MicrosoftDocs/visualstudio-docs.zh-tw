---
title: PROFILER_EVENT_MASK 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: da55371c24f6a21acbc9dc789a2c76ef6e7c66b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096664"
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK 列舉
指出應該要分析的事件類型。  
  
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|使用者撰寫的指令碼和動態程式碼中所定義的設定檔函式。|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|設定檔原生函式所定義的指令碼引擎。|  
|PROFILER_EVENT_MASK_TRACE_ALL|所有的使用者定義和指令碼引擎函式，但不包括呼叫至文件物件模型 (DOM) 中的設定檔。|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|設定檔的函式呼叫至 dom。|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|設定檔的所有功能，包括呼叫至 dom。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼 Profiler 常數、 列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)