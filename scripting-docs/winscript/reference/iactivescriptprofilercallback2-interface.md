---
title: "IActiveScriptProfilerCallback2 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 介面
提供指令碼引擎用於文件物件模型 (DOM) 的事件發生時，通知分析工具物件的方法。 實作這個介面是由程式碼剖析工具物件。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|通知分析工具物件的指令碼引擎即將執行 DOM 函式呼叫。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|通知分析工具的指令碼引擎的物件完成執行後，DOM 函式呼叫。|  
  
## <a name="remarks"></a>備註  
 `IActiveScriptProfilerCallback2`第一次釋放與 Internet Explorer 9 的介面。  
  
 不是呼叫到 DOM 的函式呼叫的通知係由[IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)。  
  
> [!NOTE]
>  若要加入的功能啟動和停止程式碼剖析執行指令碼時，呼叫下列方法。 藉由使用這些方法，您可以取得完整的呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]正在執行，當您啟動或停止分析。  
>   
>  -   呼叫[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)您已經啟動程式碼剖析，通知分析工具。  
> -   呼叫[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)通知分析工具，您很快就會停止程式碼剖析。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)