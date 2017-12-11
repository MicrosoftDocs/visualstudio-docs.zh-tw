---
title: LineOff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6914a94300cd7fdb06db8743159698047451fd74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="lineoff"></a>LineOff
根據預設，分析工具會在您使用取樣分析方法時，收集原始程式碼行號和位移資料行號。 VSPerfCmd 的 **LineOff** 選項在使用 VSPerfCmd 啟動應用程式時，會停用行號資料收集。 指定 [LineOff] 時，分析資料會收集至函式層級。  
  
 **LineOff** 只能搭配 [啟動] 選項，而且只能在已初始化分析工具，使用 [啟動]：[取樣] 選項進行取樣時。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>參數  
 無  
  
## <a name="required-options"></a>必要選項  
 **LineOff** 選項只能用在包含 [啟動] 選項的命令列中。  
  
 **Launch：** `AppName`  
 啟動指定的應用程式，並使用取樣方法開始程式碼剖析。  
  
## <a name="example"></a>範例  
 這個範例會啟動應用程式和分析工具，並停用程式碼層級的取樣。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)