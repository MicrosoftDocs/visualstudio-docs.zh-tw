---
title: 關機 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7e351050859a96ca95c267bdcbe34ee19e7f87f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488753"
---
# <a name="shutdown"></a>關機
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[關機](https://docs.microsoft.com/visualstudio/profiling/shutdown)。  
  
[關機] 選項等候任何目前已分析的處理序結束或中斷連接，然後關閉分析工具，結束分析資料檔案。 [關機] 選項必須是分析執行的最後一道命令。  
  
 如未指定逾時參數，[關機] 選項會無限期等候。 如已指定逾時參數，則此選項會在指定的秒數後傳回，不關閉分析工具或結束資料檔。  
  
 [關機] 選項必須是命令列上指定的唯一選項。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>參數  
 `Timeout`  
 -   (選擇性) 如已指定，則此選項會在指定的秒數後傳回，不關閉分析工具或結束分析資料檔。  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)



