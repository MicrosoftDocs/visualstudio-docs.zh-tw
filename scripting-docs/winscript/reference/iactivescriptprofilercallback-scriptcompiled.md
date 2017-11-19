---
title: "IActiveScriptProfilerCallback::ScriptCompiled |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
通知分析工具的指令碼引擎的物件已編譯的指令碼。 這個方法是針對每個已編譯的指令碼呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>參數  
 `scriptId`  
 [in]已編譯的指令碼的唯一識別碼。 指令碼引擎所指派這個識別碼。  
  
 `type`  
 [in]已編譯的指令碼類型。 值會定義在[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
 `pIDebugDocumentContext`  
 [in]如果有的話，指標`IUnknown`必須在查詢分析工具的介面[IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)指標。 否則，這會是 null。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。  
  
## <a name="remarks"></a>備註  
 只有當這主機所支援的指令碼引擎可以提供的文件內容。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)