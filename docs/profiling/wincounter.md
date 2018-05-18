---
title: WinCounter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4751d44afc2f54ea57866e3674a5bc150444088b
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="wincounter"></a>WinCounter
**WinCounter** 選項指定 Windows 或應用程式效能計數器在分析回合期間依設定的間隔進行收集。 在分析資料檔案中，會以標記形式列出 Windows 和應用程式效能計數器。 您可以在個別的選項中指定多個效能計數器進行收集。  
  
 根據預設，會每隔 500 毫秒收集一次計數器。 使用 **AutoMark** 選項來指定不同的收集間隔。  
  
 只能使用一個 **AutoMark** 選項。 如果指定多個 **AutoMark** 選項，則會使用最後一個。  
  
 **WinCounter** 選項只能與 **Start** 選項搭配使用。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `Path`  
 PDH 計數器路徑格式的 Windows 效能計數器。  
  
## <a name="required-options"></a>必要選項  
 **WinCounter** 選項只能與 **Start** 選項搭配使用。  
  
 **Start:** `Method`  
 **Start** 選項可將分析工具初始化為指定的分析方法。  
  
## <a name="exclusive-options"></a>專屬選項  
 **AutoMark** 選項只能與 **WinCounter** 選項搭配使用。  
  
 **AutoMark:** `Milliseconds`  
 指定 Windows 效能計數器資料收集之間的毫秒數。  
  
## <a name="example"></a>範例  
 在下列範例中，指定兩個 Windows 效能計數器依 1000 毫秒的間隔進行收集。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)