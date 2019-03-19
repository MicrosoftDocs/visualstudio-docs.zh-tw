---
title: PROFILER_SCRIPT_TYPE 列舉 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157434"
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