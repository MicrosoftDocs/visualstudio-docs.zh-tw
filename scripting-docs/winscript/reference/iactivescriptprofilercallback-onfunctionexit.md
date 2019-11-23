---
title: IActiveScriptProfilerCallback：： OnFunctionExit |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571677"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
通知 profiler 物件，腳本引擎已完成執行不是呼叫檔物件模型（DOM）的函式呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnFunctionExit(  
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
 針對 DOM 呼叫，腳本引擎會呼叫[IActiveScriptProfilerCallback2：： OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) ，而不是 `IActiveScriptProfilerCallback::OnFunctionExit`。 這是因為 DOM 中有大量的唯一方法和屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback：： OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)