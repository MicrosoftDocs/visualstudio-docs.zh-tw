---
title: IActiveScriptProfilerCallback2：： OnFunctionEnterByName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0407441c77250b2cc27e9fee09c5039bb8e44ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571634"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
通知 profiler 物件，腳本引擎即將執行檔物件模型（DOM）函式呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>參數  
 `pwszFunctionName`  
 在腳本引擎即將執行之函式的名稱。  
  
 `scriptType`  
 在函數的類型。 如需有效值的描述，請參閱[PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## <a name="return-value"></a>傳回值  
 腳本引擎會忽略這個方法的傳回值。  
  
## <a name="remarks"></a>備註  
 針對 DOM 呼叫，腳本引擎會呼叫這個方法，而不是呼叫[IActiveScriptProfilerCallback：： OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)。 這是因為 DOM 中有大量的唯一方法和屬性。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptProfilerCallback2：： OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)    
 [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)