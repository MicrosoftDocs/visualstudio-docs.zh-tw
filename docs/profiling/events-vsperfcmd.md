---
title: Events (VSPerfCmd) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84f1d515722203f15b1b667df6fb7fdf72fe4fb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
VSPerfCmd.exe **Events** 選項會控制 Windows 事件追蹤 (ETW) 記錄。 ETW 資料會儲存至與分析工具資料檔案不同的 .etl 檔案。 使用 [VSPerfReport](../profiling/vsperfreport.md) /summary:etw 命令，即可透過報表形式來檢視資料。  
  
 呼叫 VSPerfCmd **Shutdown** 命令停止分析之前，隨時都可以呼叫 **Events** 選項。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>參數  
 **On**&#124;**Off**  
 啟動或停止收集事件資料。  
  
 `Guid`  
 提供者控制項的 GUID。  
  
 `ProviderName`  
 向 Windows Management Instrumentation (WMI) 註冊的提供者名稱。  
  
 `Flags`  
 由事件提供者所定義而且前面加上 "0x" 的十六進位旗標值。  
  
 `Level`  
 指定所收集的資料量。 `Level` 是由事件提供者所定義。  
  
 **Events** 選項了解下列核心關鍵字作為提供者名稱：  
  
 **Process**  
 處理序事件  
  
 **Thread**  
 執行緒事件  
  
 **影像**  
 影像載入和卸載事件  
  
 **Disk**  
 磁碟 I/O 事件  
  
 **檔案**  
 檔案 I/O 事件  
  
 **Hardfault**  
 硬性分頁錯誤  
  
 **Pagefault**  
 軟性分頁錯誤  
  
 **Network**  
 網路事件  
  
 **Registry**  
 登錄存取事件  
  
 請注意，只能啟用核心提供者。 不可以予以停用，也不可以在關閉監視器之前修改其旗標。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  啟用 CLR ETW 事件時，也會透過「追蹤檢視」報表收集其他啟動資料。 若要排除啟動事件使其不出現在報表中，請使用下列命令：  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  如果您不要排除啟動事件，則因為這些事件不會列出在受控物件格式 (MOF) 檔案中，所以它們在報表中會顯示為 GUID。 如需詳細資訊，請參閱 Microsoft 網站上的這個頁面：[範例受控物件格式 (MOF) 檔案](http://go.microsoft.com/fwlink/?linkid=37118)。  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)