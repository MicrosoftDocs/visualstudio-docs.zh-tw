---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs
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
ms.openlocfilehash: f6fdb4addace1b0bbabdd4303c3943b976763514
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993263"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
告知指令碼引擎將會執行文件物件模型 (DOM) 函式呼叫的程式碼剖析工具物件。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>參數  
 `pwszFunctionName`  
 [in]將指令碼引擎會執行的函式名稱。  
  
 `scriptType`  
 [in]函式的類型。 如需有效值的描述，請參閱 < [PROFILER_SCRIPT_TYPE 列舉](../../winscript/reference/profiler-script-type-enumeration.md)。  
  
## <a name="return-value"></a>傳回值  
 這個方法的傳回值會忽略指令碼引擎。  
  
## <a name="remarks"></a>備註  
 DOM 呼叫指令碼引擎會呼叫這個方法，而不是呼叫[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)。 這是因為大量的 DOM 中唯一的方法和屬性  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)