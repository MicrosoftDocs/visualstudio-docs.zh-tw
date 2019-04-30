---
title: IActiveScriptProfilerCallback::OnFunctionExit |Microsoft Docs
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
ms.openlocfilehash: 9c84b64a12b1a6b61399f70b7209c86dd8d2a9a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993328"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
物件，指令碼引擎已完成執行函式呼叫，不會呼叫到文件物件模型 (DOM) 會通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>參數  
 `scriptId`  
 [in]屬於此函式的指令碼的唯一識別碼。 此識別碼會指定指令碼引擎。  
  
 `functionId`  
 [in]函式的唯一識別碼。 此識別碼會指定指令碼引擎。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。  
  
## <a name="remarks"></a>備註  
 DOM 呼叫指令碼引擎會呼叫[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)而不是`IActiveScriptProfilerCallback::OnFunctionExit`。 這是因為大量的 DOM 中唯一的方法和屬性  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)