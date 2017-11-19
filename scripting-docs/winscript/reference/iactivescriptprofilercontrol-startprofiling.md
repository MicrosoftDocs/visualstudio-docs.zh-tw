---
title: "IActiveScriptProfilerControl::StartProfiling |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5362eaba439ff7a645a8323c4eed5d9496f6d88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
啟動指令碼引擎上的分析。 指令碼引擎建立的分析工具物件執行個體，藉由呼叫[CoCreateInstance](http://msdn.microsoft.com/en-us/7295a55b-12c7-4ed0-a7a4-9ecee16afdec)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>參數  
 `clsidProfilerObject`  
 [in]類別要建立的程式碼剖析工具物件的識別項 (CLSID)。  
  
 `dwEventMask`  
 [in]4 位元組位元遮罩，指定的事件類型。 中所定義之位元[PROFILER_EVENT_MASK 列舉](../../winscript/reference/profiler-event-mask-enumeration.md)。  
  
 `dwContext`  
 [in]4 位元組值傳遞至分析工具物件。  
  
## <a name="return-value"></a>傳回值  
 會傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_PRESENT`|已啟用程式碼剖析。|  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)