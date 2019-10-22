---
title: IActiveScriptProfilerCallback：： Shutdown |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571653"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
呼叫以在腳本引擎上停止分析時，通知 profiler 物件。 如此一來，profiler 物件就可以視需要呼叫其清除常式。 當腳本引擎關閉時，或呼叫[IActiveScriptProfilerCallback：： Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)失敗時，腳本引擎也會呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>參數  
 `hrReason`  
 在關機的原因。 如果腳本引擎正在關機，則會傳遞 `S_OK`。 如果對[IActiveScriptProfilerCallback：： Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)的呼叫會傳回失敗 hresult，則會傳遞 hresult。 否則，會從[IActiveScriptProfilerControl：： StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)抓取此值。  
  
## <a name="return-value"></a>傳回值  
 腳本引擎會忽略這個方法的傳回值。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)