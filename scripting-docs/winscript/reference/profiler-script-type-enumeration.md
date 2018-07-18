---
title: PROFILER_SCRIPT_TYPE 列舉 |Microsoft 文件
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
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734118"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE 列舉
指定指令碼的類型。  
  
## <a name="syntax"></a>語法  
  
```  
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
|PROFILER_SCRIPT_TYPE_DOM|指定插入文件物件模型 (DOM) Internet Explorer 中，例如，若要呼叫的呼叫`document.getElementById`方法。|  
  
## <a name="see-also"></a>另請參閱  
 [使用中指令碼分析工具的常數、 列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)