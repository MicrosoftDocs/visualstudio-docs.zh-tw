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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574577"
---
# <a name="profiler_script_type-enumeration"></a>PROFILER_SCRIPT_TYPE 列舉
指定腳本的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|指定使用者撰寫的腳本程式碼。|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|指定在執行期間動態產生的腳本程式碼。|  
|PROFILER_SCRIPT_TYPE_NATIVE|指定腳本引擎所定義的原生函式和物件的腳本類型。|  
|PROFILER_SCRIPT_TYPE_DOM|指定對 Internet Explorer 檔物件模型（DOM）的呼叫，例如呼叫 `document.getElementById` 方法。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback：： ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [IActiveScriptProfilerCallback2：： OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)