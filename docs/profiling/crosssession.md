---
title: CrossSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 192ddfb7312dff13b457f36940220f0bb17fe2c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909251"
---
# <a name="crosssession"></a>CrossSession
*VSPerfCmd.exe* **CrossSession** 選項可讓分析工具從任何主控台工作階段中收集資料。 **CrossSession** 選項必須與 **Start** 選項搭配使用。  
  
 您可以使用縮寫 **CS** 取代 **CrossSession**。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>參數  
 無  
  
## <a name="valid-options"></a>有效選項  
 若要啟用另一個工作階段中的分析，必須指定含 **Start** 選項的 **CrossSession** 選項。 **CrossSession** 也必須指定於任何後續的 **VSPerfCmd Attach** 和 **Detach** 命令中。  
  
 **Start:** `Method`  
 **Start** 選項可將分析工具初始化為指定的分析方法。  
  
 **Attach：**_PID_[**,**_PID_]  
 開始分析指定的處理序。  
  
 **Detach**[**:**_PID_[,_PID_]]  
 停止分析指定的處理序。  
  
## <a name="example"></a>範例  
 在此範例中，**CrossSession** 選項是用來附加至已在另一個主控台工作階段中啟動的應用程式。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>另請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服務](../profiling/command-line-profiling-of-services.md)