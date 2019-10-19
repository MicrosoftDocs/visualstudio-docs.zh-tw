---
title: IActiveScriptProfilerCallback 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571709"
---
# <a name="iactivescriptprofilercallback-interface"></a>IActiveScriptProfilerCallback 介面
提供當事件發生時，腳本引擎用來通知 profiler 物件的方法。 這個介面是由 profiler 物件所執行。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|呼叫以在腳本引擎上啟動分析時，初始化 profiler 物件。|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|呼叫以在腳本引擎上停止分析時，釋放和釋放 profiler 物件。|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|通知 profiler 物件，腳本引擎已編譯腳本。|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|通知 profiler 物件，腳本引擎在編譯腳本時發現函式。|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|通知 profiler 物件，腳本引擎即將執行不是呼叫檔物件模型（DOM）的函式呼叫。|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|通知 profiler 物件，腳本引擎已完成執行不是 DOM 呼叫的函式呼叫。|  
  
## <a name="remarks"></a>備註  
 檔物件模型（DOM）中的函式呼叫通知是由[IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)所提供。  
  
> [!NOTE]
> 若要在腳本執行時加入啟動和停止分析的功能，請呼叫下列方法。 藉由使用這些方法，您可以在啟動或停止分析時，取得完整的呼叫堆疊（如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 正在執行）。  
> 
> - 呼叫[IActiveScriptProfilerControl2：： CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)以通知分析工具您已開始進行程式碼剖析。  
>   - 呼叫[IActiveScriptProfilerControl2：:P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)來通知分析工具，您很快就會停止程式碼剖析。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)