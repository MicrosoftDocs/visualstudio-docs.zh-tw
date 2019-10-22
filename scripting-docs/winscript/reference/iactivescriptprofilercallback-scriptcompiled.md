---
title: IActiveScriptProfilerCallback：： ScriptCompiled |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571657"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
通知 profiler 物件，腳本引擎已編譯腳本。 這個方法會針對每個編譯的腳本呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>參數  
 `scriptId`  
 在已編譯之腳本的唯一識別碼。 這個識別碼是由腳本引擎所指派。  
  
 `type`  
 在編譯的腳本類型。 這些值會在[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)中定義。  
  
 `pIDebugDocumentContext`  
 在如果可用，則為分析工具必須查詢[IDebugDocumentCoNtext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)指標之 `IUnknown` 介面的指標。 否則，這會是 null。  
  
## <a name="return-value"></a>傳回值  
 腳本引擎會忽略這個方法的傳回值。  
  
## <a name="remarks"></a>備註  
 只有當主機支援時，腳本引擎才能提供檔內容。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)