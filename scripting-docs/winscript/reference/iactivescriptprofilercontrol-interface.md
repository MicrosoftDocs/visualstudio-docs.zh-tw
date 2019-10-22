---
title: IActiveScriptProfilerControl 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571594"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl 介面
由支援分析的腳本引擎所執行。 通常，執行 `IActiveScriptProfilerControl` 的物件也會實[IActiveScript](../../winscript/reference/iactivescript.md)介面。 在此情況下，您可以在物件上呼叫 `IUnknown::QueryInterface` 方法，以取得 `IActiveScriptProfilerControl` 介面的控制碼。 介面提供在腳本引擎上停止和啟動程式碼剖析的必要方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|開始在腳本引擎上進行程式碼剖析。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|在腳本引擎中設定 profiler 事件遮罩。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|停止腳本引擎上的分析。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)