---
title: "IActiveScriptProfilerCallback::OnFunctionEnter |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
通知分析工具物件的指令碼引擎即將執行呼叫函式不是插入文件物件模型 (DOM) 的呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>參數  
 `scriptId`  
 [in]指令碼屬於函式的唯一識別碼。 指令碼引擎所指派這個識別碼。  
  
 `functionId`  
 [in]函式的唯一識別碼。 指令碼引擎所指派這個識別碼。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。  
  
## <a name="remarks"></a>備註  
 指令碼引擎會呼叫 DOM 呼叫[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)而不是`IActiveScriptProfilerCallback::OnFunctionEnter`。 這是因為有大量的 DOM 中唯一的方法和屬性  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)