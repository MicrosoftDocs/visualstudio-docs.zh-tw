---
title: Counter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4adc1b916fd8f796368de99f8007859b3d71e1cf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934688"
---
# <a name="counter"></a>計數器
**Counter** 選項會從處理器 (硬體) 效能計數器收集資料。  
  
- 當您使用取樣分析方法時，**Counter** 會指定晶片上的效能計數器和計數器事件的數目，用來做為取樣間隔。 當您使用取樣時，只能指定一個計數器。  
  
- 當您使用檢測分析方法時，會在分析工具報表中的個別欄位中，列出在上一個與目前收集事件之間隔內發生的計數器事件數目。 當您使用檢測時，可以指定多個 **Counter** 選項。  
  
  每個處理器類型都有一組自己的硬體效能計數器。 分析工具會定義一組幾乎所有處理器都通用的一般效能計數器。 若要列出您電腦上一般和處理器特定的計數器，請使用 VSPerfCmd **QueryCounters** 命令。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]  
```  
  
```cmd  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]  
```  
  
#### <a name="parameters"></a>參數  
 `Name`  
 計數器的名稱。 使用 VSPerfCmd.exe **/QueryCounters** 選項，來列出電腦上可用的計數器名稱。  
  
 `Reload`  
 取樣間隔中的計數器事件數目。 請勿與檢測方法搭配使用。  
  
 `FriendlyName`  
 (選擇性) 此字串可用來取代分析工具報告和檢視之欄標題中的 `Name`。  
  
## <a name="required-options"></a>必要選項  
 Counter 選項只能與下列其中一個選項搭配使用：  
  
 **Start:** `Trace`  
 將分析工具初始化以使用檢測方法。  
  
 **Launch：** `AppName`  
 啟動指定的應用程式和分析工具。 分析工具必須先初始化才能使用取樣方法。  
  
 **Attach:** `PID`  
 啟動分析工具，並將它附加至處理序 ID 所指定的處理序。 分析工具必須先初始化才能使用取樣方法。  
  
## <a name="example"></a>範例  
 取樣方法範例示範如何在一般分析工具計數器 NonHaltedCycles 的每 1000 個發生次數中，為應用程式取樣。  
  
 檢測方法範例示範如何將分析工具初始化來收集 L2InstructionFetches 計數器事件。 L2InstructionFetches 計數器名稱是處理器所特有。  
  
```cmd  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服務](../profiling/command-line-profiling-of-services.md)