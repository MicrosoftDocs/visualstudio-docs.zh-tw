---
title: ThreadOn 和 ThreadOff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19a183b9285e53a93f6fe6e44c94f5dcd14957e5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35668509"
---
# <a name="threadon-and-threadoff"></a>ThreadOn 和 ThreadOff
只有在使用檢測方法的命令列分析工作階段中，才能使用 *VSPerfCmd.exe* **ThreadOff** 和 **ThreadOn** 子命令。 **ThreadOff** 和 **ThreadOn** 會暫停和繼續分析指定的執行緒。 **ThreadOff** 會停止分析執行緒，而 **ThreadOn** 會開始分析執行緒。  
  
 在大部分的情況下，您可以將 **ThreadOn** 或 **ThreadOff** 指定為 *VSPerfCmd.exe* 命令列的唯一選項，但它們也可以與 **GlobalOn**、**GlobalOff**、**ProcessOn** 和 **ProcessOff** 子命令合併使用。  
  
 **ThreadOn** 和 **ThreadOff** 子命令可與 **GlobalOn** 和 **GlobalOff** 子命令互動，以控制命令列分析工作階段中所有處理序的資料收集，以及可與 **ProcessOn** 和 **ProcessOff** 子命令互動，以控制所指定處理序的資料收集。  
  
 **ThreadOff** 和 **ThreadOn** 子命令也會影響分析工具 API 函式操控的執行緒開始/停止計數。  
  
-   **ThreadOff** 可立即將執行緒開始/停止計數設定為 0，並因此會暫停分析。  
  
-   **ThreadOn** 可立即將執行緒開始/停止計數設定為 1，並因此會繼續分析。  
  
 如需詳細資訊，請參閱[分析工具 API](../profiling/profiling-tools-apis.md)。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### <a name="parameters"></a>參數  
 `TID`  
 要開始或停止之執行緒的整數識別碼。  
  
## <a name="valid-options"></a>有效選項  
 您可以在也包含下列子命令的命令列上指定 **ThreadOn** 和 **ThreadOff**。  
  
 **Start:** `Method`  
 初始化命令列分析工作階段，並設定指定的分析方法。  
  
 **GlobalOff**&#124;**GlobalOn**  
 在命令列分析工作階段中，停止或開始分析所有處理序。  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 停止或開始對指定的處理序進行分析。  
  
## <a name="example"></a>範例  
 在此範例中，**ThreadOff** 子命令是用來停止收集分析資料，僅收集應用程式啟動資料。  
  
```cmd  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服務](../profiling/command-line-profiling-of-services.md)