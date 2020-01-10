---
title: IActiveScriptProfilerCallback2：： OnFunctionExitByName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571628"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
通知 profiler 物件，腳本引擎已完成執行檔物件模型（DOM）函式呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>參數  
 `pwszFunctionName`  
 在腳本引擎完成執行之函式的名稱。  
  
 `scriptType`  
 在函數的類型。 如需有效值的描述，請參閱[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## <a name="return-value"></a>傳回值  
 腳本引擎會忽略這個方法的傳回值。  
  
## <a name="remarks"></a>備註  
 針對 DOM 呼叫，腳本引擎會呼叫這個方法，而不是呼叫[IActiveScriptProfilerCallback：： OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)。 這是因為 DOM 中有大量的唯一方法和屬性。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback2：： OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)