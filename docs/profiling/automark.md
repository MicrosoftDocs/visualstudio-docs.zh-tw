---
title: AutoMark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9a482d3ed09f12c623986e604951b7d7855e6e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="automark"></a>AutoMark
**AutoMark** 選項指定收集 Windows 軟體效能計數器事件之間的毫秒數。 Windows 效能計數器指定於 **WinCounter** 選項中。  
  
 只能在命令列上指定一個 **AutoMark** 選項。 請注意，**AutoMark** 所指定的 **WinCounter** 取樣間隔與主要取樣間隔無關。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>參數  
 `Milliseconds`  
 指定收集 Windows 效能計數器事件之間的毫秒數。  
  
## <a name="required-options"></a>必要選項  
 **WinCounter:** `Path`  
 指定要收集的 Windows 效能計數器。 當您要使用檢測方法時，可以指定多個 Windows 計數器。 當您要使用取樣方法時，只能指定一個軟體計數器。 **WinCounter** 選項必須指定於包含 **Start** 選項的命令列上。  
  
## <a name="example"></a>範例  
 在此範例中，針對兩個 Windows 效能計數器設定 1000 毫秒的取樣間隔。  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)