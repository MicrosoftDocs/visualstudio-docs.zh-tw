---
title: "IActiveScriptProfilerControl 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl 介面
實作支援程式碼剖析的指令碼引擎。 一般而言，該物件會實作`IActiveScriptProfilerControl`也會實作[IActiveScript](../../winscript/reference/iactivescript.md)介面。 在此情況下，您可以取得的控制代碼`IActiveScriptProfilerControl`介面，藉由呼叫`IUnknown::QueryInterface`物件上的方法。 介面會提供必要的方法，如停止和啟動指令碼引擎上的分析。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|啟動指令碼引擎上的分析。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|設定指令碼引擎中的程式碼剖析工具事件遮罩。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|停止程式碼剖析的指令碼引擎。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)