---
title: 錯誤：無法自動逐步執行至伺服器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8dcb8fa757f1cccf2f3aef6c2520e0c61da0b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682686"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>錯誤：無法自動逐步執行至伺服器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此錯誤指出：  
  
 無法自動逐步執行至伺服器。 執行遠端程序之前，未通知偵錯工具。  
  
 當您嘗試逐步執行 Web 服務 (請參閱 [逐步執行 XML Web Service](https://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)) 時，可能會發生這個錯誤。 一旦沒有正確設定 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ，便可能會發生這個錯誤。  
  
 可能的原因包括：  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式的 web.config 檔沒有將偵錯設定為 "true" (請參閱 [ASP.NET 應用程式中的偵錯模式](../debugger/how-to-enable-debugging-for-aspnet-applications.md))。  
  
- 在 Visual Studio 安裝之後，安裝了某個版本的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應該在 Visual Studio 之前安裝。 若要修正這個問題，請使用 Windows [控制台] **** 的 [程式和功能] **** 修復 Visual Studio 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)
