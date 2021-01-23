---
title: VSPerfMon | Microsoft Docs
description: 瞭解如何使用 VSPerfMon 工具來收集應用程式的效能資料。 這項工具通常是由 VSPerfCmd.exe 啟動。
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 919153699299c2f39ad0353ed484a9f9c9f46846
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719171"
---
# <a name="vsperfmon"></a>VSPerfMon
您可以使用 VSPerfMon 工具來收集應用程式的效能資料，而這項工具通常是由 *VSPerfCmd.exe* 啟動。 VSPerfMon 會顯示有關附加或中斷連結處理序的其他資訊，其在使用 VSPerfCmd 工具時無法使用。 若要檢視這項資訊，請以個別的視窗來啟動 VSPerfMon。 若要叫用 VSPerfMon，請使用下列語法︰

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 下表說明 VSPerfMon 工具選項：

|選項。|描述|
|-------------|-----------------|
|**U**|以 Unicode 撰寫重新導向的主控台輸出。  務必要優先指定此選項。|
|**OUTPUT:** `<` *檔案名稱* `>`|將輸出重新導向至指定的檔案名稱。|
|**跟蹤**|啟動效能監視器進行檢測分析。|
|**SAMPLE**|啟動效能監視器進行取樣分析。|
|**覆蓋**|啟動效能監視器進行程式碼涵蓋範圍收集。|
|**併發**|啟動效能監視器以進行資源爭用分析。|
|**USER:** `[` *網域* `\]` *使用者名稱*|允許用戶端透過指定的帳戶存取監視器。|
|**CROSSSESSION**|啟用跨工作階段進行程式碼剖析。|
|**計數器**`:cfg`|使用檢測 (TRACE) 分析方法時，指定要在每個檢測點收集 CPU 計數器。 您可以指定多個計數器選項，以收集多項計數器資料。<br /><br /> 使用下列語法指定計數器 (*cfg*) 資料：<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** 是 VSPerfCmd /QueryCounters 命令傳回的計數器名稱。<br />-   **Reload** 是計數器事件取樣間隔。 請勿搭配檢測方法使用 *Reload*。<br />-   指定之後，**FriendlyName** 會以程式碼剖析工具報表欄名取代 **CounterName**。|
|**WINCOUNTER**`:path`|指定要加入標記資料的 Windows 效能計數器。 `path` 是 PDH 計數器路徑格式的 Windows 效能計數器字串。 例如：<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|
|**AUTOMARK**`:n`|指定使用 /WINCOUNTER 時自動標記之間的時間間隔 (以毫秒為單位)。 捨入為最接近的 500ms。<br /><br /> 使用 0 即可停用自動標記。 (如果未指定則為預設的 500ms)|

## <a name="see-also"></a>另請參閱
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [效能報表檢視](../profiling/performance-report-views.md)
