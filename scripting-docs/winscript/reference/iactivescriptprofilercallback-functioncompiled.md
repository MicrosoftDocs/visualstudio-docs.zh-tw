---
title: "IActiveScriptProfilerCallback::FunctionCompiled |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 797476d4892224ad0b27c9caf579c0704693c835
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
遇到函式物件的指令碼引擎編譯指令碼時通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]函式的唯一識別碼。 指令碼引擎所指派這個識別碼。  
  
 `scriptId`  
 [in]指令碼屬於函式的唯一識別碼。  
  
 `pwszFunctionName`  
 [in]匿名函式的函式或為 null 的名稱。  
  
 `pwszFunctionNameHint`  
 [in]推斷的名稱的函式，或如果指令碼引擎不會推斷的任何名稱為 null。  
  
 `pIDebugDocumentContext`  
 [in]如果有的話，將指標`IUnknown`必須在查詢分析工具的介面[IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)指標。 否則為 null。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。  
  
## <a name="remarks"></a>備註  
 只有當這主機所支援的指令碼引擎可以提供的文件內容。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)