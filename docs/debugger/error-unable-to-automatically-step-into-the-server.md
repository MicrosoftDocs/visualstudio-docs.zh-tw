---
title: 錯誤： 無法自動逐步執行至伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9e7b3c45e49425c07c545f2a04673887fc8cac7
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44278669"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>錯誤：無法自動逐步執行至伺服器
這個錯誤顯示為：  
  
 無法自動逐步執行至伺服器。 執行遠端程序之前，未通知偵錯工具。  
  
 當您嘗試逐步執行 web 服務時，會發生此錯誤 (請參閱[逐步執行 XML Web Service](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764))。 一旦沒有正確設定 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ，便可能會發生這個錯誤。  
  
 可能的原因包括：  
  
-   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式的 web.config 檔沒有將偵錯設定為 "true" (請參閱 [ASP.NET 應用程式中的偵錯模式](../debugger/how-to-enable-debugging-for-aspnet-applications.md))。  
  
-   在 Visual Studio 安裝之後，安裝了某個版本的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應該在 Visual Studio 之前安裝。 若要修正此問題，請使用 Windows**控制台 > 程式和功能**修復 Visual Studio 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)