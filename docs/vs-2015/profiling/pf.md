---
title: PF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 243d5fada7342bc05d8768a7e33cca6f55e309ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442471"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe 的 **PF** 選項會將取樣的分析事件設定為分頁錯誤，並且選擇性地變更取樣間隔的分頁錯誤數目，預設值為 10。  
  
> [!NOTE]
> 64 位元系統上不能使用 PF。  
  
 **請注意：** 64 位元電腦不支援 PF。**PF** 只能用於也包含 [啟動]  或 [附加]  選項的命令列。  
  
 預設會將取樣事件設定為未暫止處理器時脈週期，並將取樣間隔設定為 10,000,000。 [計時器]  、[PF]  、[Sys]  和 [計數器]  選項可讓您設定取樣事件和取樣間隔。 **GC** 選項會在每個配置和記憶體回收事件發生時，收集 .NET 記憶體資料。 您只能在命令列上指定上述其中一個選項。  
  
 取樣事件和取樣間隔只能在包含 [啟動]  或 [附加]  選項的第一個命令列中設定。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `Events`  
 指定取樣間隔中分頁錯誤事件數目的整數值。 如果未指定 `Events`，間隔會設定為 10。  
  
## <a name="required-options"></a>必要選項  
 **PF** 只能在包含下列其中一個選項的命令列上指定。  
  
 **Launch：** `AppName`  
 啟動分析工具及 AppName 指定的應用程式。  
  
 **Attach:** `PID`  
 將分析工具附加至 AppName 指定的處理序。  
  
## <a name="invalid-options"></a>無效的選項  
 下列選項無法在與 **PF** 相同的命令列上指定。  
  
 **Timer**[ **:** `Cycles`]  
 將取樣事件設定為處理器時脈週期，並且選擇性地將取樣間隔設定為 `Cycles`。 預設的計時器間隔為 10,000,000。  
  
 **Sys**[ **:** `Events`]  
 將取樣事件設定為從已分析應用程式呼叫作業系統核心 (syscalls)，並選擇性地將取樣間隔設定為 `Events`。 預設的 Sys 間隔為 10。  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 將取樣事件設定為 `Name` 所指定的 CPU 效能計數器，並將取樣間隔設定為 `Reload`。  
  
 **GC**[ **:** {**Allocation**&#124;**Lifetime**}]  
 收集 .NET 記憶體資料。 根據預設 (**配置**)，系統會在每個記憶體配置事件發生時收集資料。 指定 **Lifetime** 參數時，也會在每個記憶體回收事件發生時收集資料。  
  
## <a name="example"></a>範例  
 此範例示範如何將分析取樣事件設定為分頁錯誤，並將取樣間隔設定為 20 個分頁錯誤。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)
