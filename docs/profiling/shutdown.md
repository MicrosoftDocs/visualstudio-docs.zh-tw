---
title: 關機 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 045f84542334b16d7e3d57fb48099e61f144cadd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992330"
---
# <a name="shutdown"></a>關機
[關機] 選項會等候任何目前分析的處理序結束或中斷連結，然後關閉分析工具及關閉分析資料檔案。 [關機] 選項必須是分析執行的最後一道命令。  
  
 如未指定逾時參數，[關機] 選項會無限期等候。 如已指定逾時參數，則此選項會在指定的秒數後傳回，而不關閉分析工具或資料檔案。  
  
 [關機] 選項必須是命令列上指定的唯一選項。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>參數  
 `Timeout`  
 -   (選擇性) 如已指定，則此選項會在指定的秒數後傳回，而不關閉分析工具或關閉分析資料檔案。  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服務](../profiling/command-line-profiling-of-services.md)