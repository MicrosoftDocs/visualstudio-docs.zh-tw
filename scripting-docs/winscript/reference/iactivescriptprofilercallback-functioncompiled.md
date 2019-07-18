---
title: IActiveScriptProfilerCallback::FunctionCompiled |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a039f7a682babebdccad276adce55e69bb8e0bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993315"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
編譯指令碼時，指令碼引擎的物件會發生函式會通知分析工具。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in]函式的唯一識別碼。 此識別碼會指定指令碼引擎。  
  
 `scriptId`  
 [in]屬於此函式的指令碼的唯一識別碼。  
  
 `pwszFunctionName`  
 [in]匿名函式名稱的函式，則為 null。  
  
 `pwszFunctionNameHint`  
 [in]函式或如果指令碼引擎不會推斷的任何名稱為 null 的推斷的名稱。  
  
 `pIDebugDocumentContext`  
 [in]如果有的話，將指標`IUnknown`分析工具必須查詢的介面[IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)指標。 否則為 null。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。  
  
## <a name="remarks"></a>備註  
 指令碼引擎可以提供的文件內容，只有當主應用程式支援此功能。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)