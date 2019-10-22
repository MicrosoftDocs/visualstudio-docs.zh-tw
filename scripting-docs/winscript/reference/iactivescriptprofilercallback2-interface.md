---
title: IActiveScriptProfilerCallback2 介面 |Microsoft Docs
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
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577306"
---
# <a name="iactivescriptprofilercallback2-interface"></a>IActiveScriptProfilerCallback2 介面
提供在發生檔物件模型（DOM）事件時，腳本引擎用來通知 profiler 物件的方法。 這個介面是由 profiler 物件所執行。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|通知 profiler 物件，腳本引擎即將執行 DOM 函式呼叫。|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|通知 profiler 物件，腳本引擎已完成執行 DOM 函數呼叫。|  
  
## <a name="remarks"></a>備註  
 第一次使用 Internet Explorer 9 發行 `IActiveScriptProfilerCallback2` 介面。  
  
 [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)會提供未呼叫 DOM 的函式呼叫通知。  
  
> [!NOTE]
> 若要在腳本執行時加入啟動和停止分析的功能，請呼叫下列方法。 藉由使用這些方法，您可以在啟動或停止分析時，取得完整的呼叫堆疊（如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 正在執行）。  
> 
> - 呼叫[IActiveScriptProfilerControl2：： CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)以通知分析工具您已開始進行程式碼剖析。  
>   - 呼叫[IActiveScriptProfilerControl2：:P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)來通知分析工具，您很快就會停止程式碼剖析。  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)