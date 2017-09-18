---
title: "錯誤：未正確設定 Web 伺服器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.projnotconfigured"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, Web 應用程式錯誤"
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 錯誤：未正確設定 Web 伺服器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可能導致本錯誤的原因包括：  
  
-   嘗試偵錯已複製到不同電腦、已手動重新命名或已移動的 .NET Web 應用程式。  
  
-   沒有足夠的 IIS 連接。 如需將網站部署至 IIS 的詳細資訊，請參閱[建立網站](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site)。  
  
-   如果您嘗試偵錯 ASP.NET 應用程式，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)，取得部署到執行 IIS 8 或更高版本之遠端電腦的指示，或參閱[在執行 IIS 7.5 的遠端電腦上遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)取得部署到執行 IIS 7.5 之遠端電腦的指示。  
  
## 請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)