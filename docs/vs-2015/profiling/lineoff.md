---
title: LineOff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbe8a715c5bb179c5293dd666f1879c07068d8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583167"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

根據預設，分析工具會在您使用取樣分析方法時，收集原始程式碼行號和位移資料行號。 VSPerfCmd 的 **LineOff** 選項在使用 VSPerfCmd 啟動應用程式時，會停用行號資料收集。 指定 [LineOff]**** 時，分析資料會收集至函式層級。  
  
 **LineOff** 只能搭配 [啟動]**** 選項，而且只能在已初始化分析工具，使用 [啟動]****：[取樣]**** 選項進行取樣時。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>參數  
 無  
  
## <a name="required-options"></a>必要選項  
 **LineOff** 選項只能用在包含 [啟動]**** 選項的命令列中。  
  
 **啟動：**`AppName`  
 啟動指定的應用程式，並使用取樣方法開始程式碼剖析。  
  
## <a name="example"></a>範例  
 這個範例會啟動應用程式和分析工具，並停用程式碼層級的取樣。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>另請參閱  
 [>vsperfcmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)
