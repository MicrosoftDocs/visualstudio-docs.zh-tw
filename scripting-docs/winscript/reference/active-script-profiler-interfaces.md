---
title: 動態指令碼 Profiler 介面 |Microsoft Docs
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
ms.openlocfilehash: eeadf0de5563a4882c067960559414167e729173
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422238"
---
# <a name="active-script-profiler-interfaces"></a>動態指令碼分析工具的介面
作用中的指令碼 Profiler 介面可讓您能夠接收從程式碼剖析事件[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]引擎。  
  
 Activprof.h 標頭檔會提供此節列出的介面。  
  
## <a name="in-this-section"></a>本節內容  
 下列介面啟用分析：  
  
- [IActiveScriptProfilerControl 介面](../../winscript/reference/iactivescriptprofilercontrol-interface.md)  
  
- [IActiveScriptProfilerControl2 介面](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)  
  
- [IActiveScriptProfilerControl3 介面](../../winscript/reference/iactivescriptprofilercontrol3-interface.md)  
  
- [IActiveScriptProfilerControl5 介面](../../winscript/reference/iactivescriptprofilercontrol5-interface.md)  
  
- [IActiveScriptProfilerCallback 介面](../../winscript/reference/iactivescriptprofilercallback-interface.md)  
  
- [IActiveScriptProfilerCallback2 介面](../../winscript/reference/iactivescriptprofilercallback2-interface.md)  
  
- [IActiveScriptProfilerCallback3 介面](../../winscript/reference/iactivescriptprofilercallback3-interface.md)  
  
- [IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)  
  
  下節列出用於程式碼剖析的列舉型別：  
  
- [動態指令碼分析工具的常數、列舉和結構](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)  
  
> [!NOTE]
> Internet Explorer 8 初次發行時使用中的指令碼 Profiler 介面。 `IActiveScriptProfilerControl2`和`IActiveScriptProfilerCallback2`Internet Explorer 9 初次發行介面。 [IActiveScriptProfilerControl3 介面](../../winscript/reference/iactivescriptprofilercontrol3-interface.md)， [IActiveScriptProfilerCallback3 介面](../../winscript/reference/iactivescriptprofilercallback3-interface.md)，並[IActiveScriptProfilerHeapEnum 介面](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)介面第一次釋放與 Internet Explorer 10。 [IActiveScriptProfilerControl5 介面](../../winscript/reference/iactivescriptprofilercontrol5-interface.md)使用 Internet Explorer 11 首次發行。  
>   
> 在 Internet Explorer 8 和 Internet Explorer 9，只有[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]語言以支援指令碼分析會使用這些介面。  
  
## <a name="see-also"></a>另請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)