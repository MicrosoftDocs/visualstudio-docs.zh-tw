---
title: PROFILER_SCRIPT_TYPE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac387af4601ff822982c10e61f9813b2db7e8047
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086902"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE 列舉
指定指令碼的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|指定使用者撰寫的指令碼。|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|指定在執行期間以動態方式產生的指令碼。|  
|PROFILER_SCRIPT_TYPE_NATIVE|指定原生函式和指令碼引擎所定義的物件的指令碼類型。|  
|PROFILER_SCRIPT_TYPE_DOM|指定呼叫到文件物件模型 (DOM) 的 Internet Explorer，例如，若要呼叫`document.getElementById`方法。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼 Profiler 常數、 列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)