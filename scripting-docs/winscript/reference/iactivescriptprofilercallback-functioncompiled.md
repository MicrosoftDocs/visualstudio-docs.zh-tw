---
title: IActiveScriptProfilerCallback：： FunctionCompiled |Microsoft Docs
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
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576467"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
通知 profiler 物件，腳本引擎在編譯腳本時發現函式。  
  
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
 在函式的唯一識別碼。 這個識別碼是由腳本引擎所指派。  
  
 `scriptId`  
 在函數所屬腳本的唯一識別碼。  
  
 `pwszFunctionName`  
 在函式的名稱，如果是匿名函數則為 null。  
  
 `pwszFunctionNameHint`  
 在函數的推斷名稱，如果腳本引擎未推斷任何名稱，則為 null。  
  
 `pIDebugDocumentContext`  
 在如果可用，則為分析工具必須查詢[IDebugDocumentCoNtext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)指標之 `IUnknown` 介面的指標。 否則為 null。  
  
## <a name="return-value"></a>傳回值  
 腳本引擎會忽略這個方法的傳回值。  
  
## <a name="remarks"></a>備註  
 只有當主機支援時，腳本引擎才能提供檔內容。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)