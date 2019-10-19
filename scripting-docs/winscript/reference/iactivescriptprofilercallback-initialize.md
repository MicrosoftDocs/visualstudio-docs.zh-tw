---
title: IActiveScriptProfilerCallback：： Initialize |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576448"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
呼叫以在腳本引擎上啟動分析時，初始化 profiler 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>參數  
 `dwContext`  
 在傳遞至[IActiveScriptProfilerControl：： StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)的4位元組值。  
  
## <a name="return-value"></a>傳回值  
 傳回 HRESULT。 可能的值如下：  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 如果方法無法初始化 profiler 物件，它應該會傳回失敗 HRESULT 來通知腳本引擎。 在此情況下，腳本引擎應該直接呼叫[IActiveScriptProfilerCallback：： Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)，在參數中傳遞 HRESULT，然後釋放 profiler 物件。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)