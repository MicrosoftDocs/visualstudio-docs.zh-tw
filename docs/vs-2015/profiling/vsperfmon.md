---
title: VSPerfMon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a06a6632d62f853eef33cad00ad766e0d1aab87
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54776049"
---
# <a name="vsperfmon"></a>VSPerfMon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 VSPerfMon 工具來收集應用程式的效能資料，而這項工具通常是由 VSPerfCmd.exe 啟動。 VSPerfMon 會顯示有關附加或中斷連結處理序的其他資訊，其在使用 VSPerfCmd 工具時無法使用。 若要檢視這項資訊，請以個別的視窗來啟動 VSPerfMon。 若要叫用 VSPerfMon，請使用下列語法︰  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 下表說明 VSPerfMon 工具選項：  
  
|選項|描述|  
|-------------|-----------------|  
|**U**|以 Unicode 撰寫重新導向的主控台輸出。  務必要優先指定此選項。|  
|**OUTPUT:** `<` *檔案名稱* `>`|將輸出重新導向至指定的檔案名稱。|  
|**TRACE**|啟動效能監視器進行檢測分析。|  
|**SAMPLE**|啟動效能監視器進行取樣分析。|  
|**COVERAGE**|啟動效能監視器進行程式碼涵蓋範圍收集。|  
|**CONCURRENCY**|啟動效能監視器以進行資源爭用分析。|  
|**USER:** `[` *網域* `\]` *使用者名稱*|允許用戶端透過指定的帳戶存取監視器。|  
|**CROSSSESSION**|啟用跨工作階段進行程式碼剖析。|  
|**COUNTER** `:cfg`|使用檢測 (TRACE) 分析方法時，指定要在每個檢測點收集 CPU 計數器。 您可以指定多個計數器選項，以收集多項計數器資料。<br /><br /> 使用下列語法指定計數器 (*cfg*) 資料：<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** 是 VSPerfCmd /QueryCounters 命令傳回的計數器名稱。<br />-   **Reload** 是計數器事件取樣間隔。 請勿搭配檢測方法使用 *Reload*。<br />-   指定之後，**FriendlyName** 會以程式碼剖析工具報表欄名取代 **CounterName**。|  
|**WINCOUNTER** `:path`|指定要加入標記資料的 Windows 效能計數器。 `path` 是 PDH 計數器路徑格式的 Windows 效能計數器字串。 例如：<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|  
|**AUTOMARK** `:n`|指定使用 /WINCOUNTER 時自動標記之間的時間間隔 (以毫秒為單位)。 捨入為最接近的 500ms。<br /><br /> 使用 0 即可停用自動標記。 (如果未指定則為預設的 500ms)|  
  
## <a name="see-also"></a>請參閱  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [效能報告檢視](../profiling/performance-report-views.md)
