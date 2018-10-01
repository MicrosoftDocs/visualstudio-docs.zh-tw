---
title: WinCounter | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9a8e381ed058c30dcbf1760f380cf065c1443cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496422"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[WinCounter](https://docs.microsoft.com/visualstudio/profiling/wincounter)。  
  
**WinCounter** 選項指定 Windows 或應用程式效能計數器在分析回合期間依設定的間隔進行收集。 在分析資料檔案中，會以標記形式列出 Windows 和應用程式效能計數器。 您可以在個別的選項中指定多個效能計數器進行收集。  
  
 根據預設，會每隔 500 毫秒收集一次計數器。 使用 **AutoMark** 選項來指定不同的收集間隔。  
  
 只能使用一個 **AutoMark** 選項。 如果指定多個 **AutoMark** 選項，則會使用最後一個。  
  
 **WinCounter** 選項只能與 **Start** 選項搭配使用。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)



