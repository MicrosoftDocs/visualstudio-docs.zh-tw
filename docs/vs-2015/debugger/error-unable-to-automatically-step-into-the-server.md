---
title: 錯誤： 無法自動逐步執行至伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d75ed4ddb42705b95a5ddd834596bc828e0f3ec2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485445"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>錯誤：無法自動逐步執行至伺服器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[錯誤： 無法將自動步驟到伺服器](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-automatically-step-into-the-server)。  
  
這個錯誤顯示為：  
  
 無法自動逐步執行至伺服器。 執行遠端程序之前，未通知偵錯工具。  
  
 當您嘗試逐步執行 Web 服務 (請參閱 [逐步執行 XML Web Service](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)) 時，可能會發生這個錯誤。 一旦沒有正確設定 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]，便可能會發生這個錯誤。  
  
 可能的原因包括：  
  
-   Web.config 檔案您[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]應用程式中未設定為"true"的偵錯 (請參閱 < [ASP.NET 應用程式中的 偵錯模式下](../debugger/how-to-enable-debugging-for-aspnet-applications.md))。  
  
-   版本[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]安裝 Visual Studio 之後，安裝。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應該在 Visual Studio 之前安裝。 若要修正這個問題，請使用 Windows [控制台] 的 [程式和功能]  修復 Visual Studio 安裝。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)



