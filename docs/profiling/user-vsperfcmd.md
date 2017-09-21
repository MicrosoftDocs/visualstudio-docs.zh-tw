---
title: "User (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# User (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**User** 選項會指定帳戶的網域和使用者名稱，該帳戶擁有已進行過程式碼剖析的處理序。  只有在處理序是以非登入使用者的身分執行時，才需要這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。  
  
 **User** 選項只能在也包含 **Start** 選項的命令列上指定。  
  
## 語法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### 參數  
 `Domain`  
 使用者的網域名稱。  
  
 `UserName`  
 使用者的名稱。  
  
## 必要選項  
 **User** 選項只能與 **Start** 選項搭配使用。  
  
 **Start:** `Method`  
 將程式碼剖析工具初始化成指定的程式碼剖析方法。  
  
## 範例  
 下列範例示範 **User** 選項的用法。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)