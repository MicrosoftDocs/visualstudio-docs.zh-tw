---
title: "輸出 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7452ad6aa8d7f190eebbc35d4be087c14dcd51a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="output"></a>輸出
[輸出] 選項指定效能工作階段的分析資料檔案名稱。 [輸出] 必須搭配 [啟動] 選項。  
  
## <a name="syntax"></a>語法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `FileName`  
 資料檔案的名稱。 可接受完整和部分路徑。 如未指定路徑，即會在目前的目錄中建立檔案。  
  
## <a name="required-options"></a>必要選項  
 [輸出] 選項必須搭配 [啟動] 選項。  
  
 **Start:** `Method`  
 指定輸出檔名稱。  
  
## <a name="example"></a>範例  
 在以下範例中，分析資料檔案是建立在目前的目錄中。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)