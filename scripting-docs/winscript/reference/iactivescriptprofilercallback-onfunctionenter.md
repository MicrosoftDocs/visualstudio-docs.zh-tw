---
title: IActiveScriptProfilerCallback：： OnFunctionEnter |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6157638353712d6f376fa1eb46a68980b493a5c3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571694"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
通知 profiler 物件，腳本引擎即將執行不是呼叫檔物件模型（DOM）的函式呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>參數  
 `scriptId`  
 在函數所屬腳本的唯一識別碼。 這個識別碼是由腳本引擎所指派。  
  
 `functionId`  
 在函式的唯一識別碼。 這個識別碼是由腳本引擎所指派。  
  
## <a name="return-value"></a>傳回值  
 腳本引擎會忽略這個方法的傳回值。  
  
## <a name="remarks"></a>備註  
 針對 DOM 呼叫，腳本引擎會呼叫[IActiveScriptProfilerCallback2：： OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) ，而不是 `IActiveScriptProfilerCallback::OnFunctionEnter`。 這是因為 DOM 中有大量的唯一方法和屬性。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerCallback：： OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)    
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)