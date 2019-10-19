---
title: IActiveScriptProfilerControl：： StopProfiling |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5900678093d57b3c995ac3bca8464ccd612fb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571547"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
停止腳本引擎上的分析。 這個方法會在 profiler 物件上呼叫[IActiveScriptProfilerCallback：： Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) ，然後釋放它。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>參數  
 `hrShutdownReason`  
 在要當做參數傳遞至 profiler 物件之[IActiveScriptProfilerCallback：： Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)方法的 HRESULT。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|未啟用程式碼剖析。|  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)