---
title: 動態指令碼分析工具介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ab8a1f0d-393c-4d6a-94c1-d5b8aa76788c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9395c392051e184bf61bea65e7ef7ac3c3fe2c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572675"
---
# <a name="active-script-profiler-interfaces"></a>動態指令碼分析工具的介面
動態指令碼分析工具介面可讓您接收來自 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎的程式碼剖析事件。  
  
 Activprof 標頭檔提供本節所列的介面。  
  
## <a name="in-this-section"></a>本章節內容  
 下列介面會啟用分析：  
  
- [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
  
- [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)  
  
- [IActiveScriptProfilerControl3 介面](../../winscript/reference/iactivescriptprofilercontrol3-interface.md)  
  
- [IActiveScriptProfilerControl5 介面](../../winscript/reference/iactivescriptprofilercontrol5-interface.md)  
  
- [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)  
  
- [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)  
  
- [IActiveScriptProfilerCallback3 介面](../../winscript/reference/iactivescriptprofilercallback3-interface.md)  
  
- [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)  
  
  下一節列出用於分析的列舉：  
  
- [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)  
  
> [!NOTE]
> 使用中的腳本分析工具介面首次與 Internet Explorer 8 一併發行。 @No__t_0 和 `IActiveScriptProfilerCallback2` 介面首次與 Internet Explorer 9 一起發行。 [IActiveScriptProfilerControl3 介面](../../winscript/reference/iactivescriptprofilercontrol3-interface.md)、 [IActiveScriptProfilerCallback3 介面](../../winscript/reference/iactivescriptprofilercallback3-interface.md)和[IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)介面首次與 Internet Explorer 10 一起發行。 第一次使用 Internet Explorer 11 發行[IActiveScriptProfilerControl5 介面](../../winscript/reference/iactivescriptprofilercontrol5-interface.md)。  
>   
> 在 Internet Explorer 8 和 Internet Explorer 9 中，只有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 語言會使用這些介面來支援腳本分析。  
  
## <a name="see-also"></a>請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)