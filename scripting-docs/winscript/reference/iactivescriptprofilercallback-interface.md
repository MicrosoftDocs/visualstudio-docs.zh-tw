---
title: IActiveScriptProfilerCallback 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2511b3e622dfa977c0ed05212203ad59fb0e71bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912615"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback 介面
提供指令碼引擎用來通知分析工具物件發生事件的方法。 分析工具物件會實作這個介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|呼叫程式碼剖析指令碼引擎上啟動時初始化分析工具物件。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|呼叫以釋放，並釋出的程式碼剖析工具物件，只要在指令碼引擎上停止分析。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|通知分析工具物件，指令碼引擎編譯指令碼。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|編譯指令碼時，指令碼引擎的物件會發生函式會通知分析工具。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|告知指令碼引擎即將執行不到文件物件模型 (DOM) 會呼叫的函式呼叫的程式碼剖析工具物件。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|通知分析工具物件，指令碼引擎已完成執行函式呼叫，不會呼叫至 dom。|  
  
## <a name="remarks"></a>備註  
 所提供的函式呼叫到文件物件模型 (DOM) 的通知[IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)。  
  
> [!NOTE]
>  若要新增至啟動和停止指令碼執行時，程式碼剖析功能，請呼叫下列方法。 藉由使用這些方法，您可以取得的完整呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]當您啟動或停止程式碼剖析執行。  
> 
> - 呼叫[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)通知分析工具，您已開始分析。  
>   -   呼叫[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)通知分析工具，您很快就會停止分析。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)