---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64bcd93e6d9045558c231c3b47ff967ffe14c078
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** 選項會列出電腦可用的 CPU (硬體) 效能計數器。  
  
 **QueryCounters** 必須是命令列上唯一的選項。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>參數  
 無  
  
## <a name="remarks"></a>備註  
 當您使用檢測方法時，分析工具可以收集每個資料集合事件的一或多個 CPU 效能計數器的值。 當您使用取樣分析方法時，您可以指定一個計數器事件和事件發生次數，用做取樣間隔。  
  
 不同的處理器會公開不同的 CPU 效能計數器。 分析工具會定義一組幾乎所有處理器都可使用的一般計數器。 [QueryCounters] 選項會列出一般計數器名稱和處理器專用計數器名稱。  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)