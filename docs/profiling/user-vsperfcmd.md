---
title: User (VSPerfCmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b96005f0935f0d1a50233196aa01bf157b6e0cd
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
**User** 選項指定擁有已分析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。  
  
 **User** 選項只能指定於也包含 **Start** 選項的命令列。  
  
## <a name="syntax"></a>語法  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>參數  
 `Domain`  
 使用者網域的名稱。  
  
 `UserName`  
 使用者的名稱。  
  
## <a name="required-options"></a>必要選項  
 **User** 選項只能與 **Start** 選項搭配使用。  
  
 **Start:** `Method`  
 將分析工具初始化為指定的分析方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **User** 選項。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)