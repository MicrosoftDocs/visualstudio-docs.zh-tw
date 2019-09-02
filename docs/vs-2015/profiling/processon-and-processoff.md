---
title: ProcessOn 和 ProcessOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77e21a280700520b6861dd42e01a4aefa4faa704
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180196"
---
# <a name="processon-and-processoff"></a>ProcessOn 和 ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe 的 **ProcessOff** 和 **ProcessOn** 子命令會暫停和繼續分析命令列分析工作階段中指定的處理序。 **ProcessOff** 會停止分析處理序，**ProcessOn** 則開始分析處理序。  
  
 在大部分的情況下，您可以將 **ProcessOn** 或 **ProcessOff** 指定為 VSPerfCmd.exe 命令列的唯一選項，但它們也可以和 **GlobalOn**、**GlobalOff**、**ThreadOn** 及 **ThreadOff** 子命令合併使用。  
  
 **ProcessOn** 和 **ProcessOff** 子命令可與 **GlobalOn** 和 **GlobalOff** 子命令互動，控制命令列分析工作階段中所有處理序的資料收集，與 **ThreadOn** 和 **ThreadOff** 子命令互動，控制指定執行緒的資料收集。  
  
 **ProcessOff** 和 **ProcessOn** 子命令也會影響分析工具 API 函式操控的處理序開始/停止計數。  
  
- **ProcessOff** 可立即將處理序開始/停止計數設定為 0，並因此會暫停分析。  
  
- **ProcessOn** 可立即將處理序開始/停止計數設定為 1，並因此會繼續分析。  
  
  如需詳細資訊，請參閱[程式碼剖析工具 API](../profiling/profiling-tools-apis.md)。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>參數  
 `PID`  
 開始或停止處理序的整數識別碼。 處理序識別碼會列在 Windows 工作管理員的 [處理序] 索引標籤。  
  
## <a name="required-subcommands"></a>必要的子命令  
 None  
  
## <a name="valid-subcommands"></a>有效的子命令  
 您可以在也包含下列子命令的命令列上指定 **ProcessOn** 和 **ProcessOff**。  
  
 **Start:** `Method`  
 初始化命令列分析工作階段，並設定指定的分析方法。  
  
 **Launch：** `AppName`  
 啟動指定的應用程式，並使用取樣方法開始程式碼剖析。  
  
 **Attach:** `PID`  
 開始對指定的處理序進行分析。  
  
 **GlobalOff**&#124;**GlobalOn**  
 在命令列分析工作階段中，停止或開始分析所有處理序。  
  
 {**ThreadOff**&#124;**ThreadOn**} **:** `TID`  
 停止或開始對指定的執行緒進行分析 (僅檢測方法)。  
  
## <a name="example"></a>範例  
 在此範例中，**ProcessOff** 子命令是用來收集應用程式啟動的分析資料。  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)
