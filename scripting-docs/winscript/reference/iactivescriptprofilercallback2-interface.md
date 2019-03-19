---
title: IActiveScriptProfilerCallback2 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d95c3db11551eb6551f509b4afbe52a70ff55ab9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145730"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 介面
提供指令碼引擎用來通知分析工具物件，Document Object Model (DOM) 的事件發生時的方法。 分析工具物件會實作這個介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|告知指令碼引擎會執行 DOM 函式呼叫的程式碼剖析工具物件。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|指令碼引擎的物件完成執行 DOM 函式呼叫會通知分析工具。|  
  
## <a name="remarks"></a>備註  
 `IActiveScriptProfilerCallback2`第一次釋放與 Internet Explorer 9 的介面。  
  
 所提供的不是載入 DOM 中呼叫的函式呼叫的通知[IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)。  
  
> [!NOTE]
>  若要新增至啟動和停止指令碼執行時，程式碼剖析功能，請呼叫下列方法。 藉由使用這些方法，您可以取得的完整呼叫堆疊如果[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]當您啟動或停止程式碼剖析執行。  
> 
> - 呼叫[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)通知分析工具，您已開始分析。  
>   -   呼叫[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)通知分析工具，您很快就會停止分析。  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)