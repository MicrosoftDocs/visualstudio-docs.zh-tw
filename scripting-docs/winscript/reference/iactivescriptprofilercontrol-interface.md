---
title: IActiveScriptProfilerControl Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7caa09f384ce460a3e73b21b10d6d8022182dde7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349487"
---
# <a name="iactivescriptprofilercontrol-interface"></a>IActiveScriptProfilerControl 介面
藉由支援程式碼剖析的指令碼引擎。 一般而言，該物件會實作`IActiveScriptProfilerControl`也會實作[IActiveScript](../../winscript/reference/iactivescript.md)介面。 在此情況下，您可以在其中取得的控制代碼`IActiveScriptProfilerControl`介面，藉由呼叫`IUnknown::QueryInterface`物件上的方法。 介面會提供所需的方法，如停止和啟動指令碼引擎上進行分析。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|啟動指令碼引擎上進行分析。|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|設定分析工具事件遮罩中的指令碼引擎。|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|停止指令碼引擎上進行分析。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼分析工具介面](../../winscript/reference/active-script-profiler-interfaces.md)