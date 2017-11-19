---
title: "IActiveScriptProfilerCallback 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback 介面
提供指令碼引擎用於事件發生時，通知分析工具物件的方法。 實作這個介面是由程式碼剖析工具物件。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|呼叫以初始化分析工具物件，每當程式碼剖析指令碼引擎已啟動。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|呼叫以釋出和釋放分析工具物件，每當程式碼剖析指令碼引擎已停止。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|通知分析工具的指令碼引擎的物件已編譯的指令碼。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|遇到函式物件的指令碼引擎編譯指令碼時通知分析工具。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|通知分析工具物件的指令碼引擎即將執行呼叫函式不是插入文件物件模型 (DOM) 的呼叫。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|通知分析工具物件完成執行函式的指令碼引擎呼叫，不是呼叫至 dom。|  
  
## <a name="remarks"></a>備註  
 所提供的函式呼叫插入文件物件模型 (DOM) 通知[IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)。  
  
> [!NOTE]
>  若要加入的功能啟動和停止程式碼剖析執行指令碼時，呼叫下列方法。 藉由使用這些方法，您可以取得完整的呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]正在執行，當您啟動或停止分析。  
>   
>  -   呼叫[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)您已經啟動程式碼剖析，通知分析工具。  
> -   呼叫[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)通知分析工具，您很快就會停止程式碼剖析。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)