---
title: 嘗試聯繫遠端電腦時，發生 DCOM 錯誤。 存取遭到拒絕。 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156523"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>嘗試聯繫遠端電腦時，發生 DCOM 錯誤。 存取遭到拒絕。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在下列情況下，遠端偵錯會使用 DCOM 在本機與遠端電腦之間進行通訊：  
  
- 在 [**工具]/[選項]/[調試**程式] 頁面中，偵錯工具設為**原生相容性模式**或**受管理的相容性模式**  
  
- 您正在偵錯 Managed C++ (C++/CLI) 程式碼。  
  
- 在 Visual Studio 2013 中，在 [**工具]/[選項]/[調試**程式] 頁面中選取 [**啟用原生編輯後繼續**]  
  
- 某些協力廠商偵錯情節  
  
  Visual Studio 處理序無法透過 DCOM 對遠端偵錯工具處理序進行自我驗證 (或認為提供的認證不足) 時，就會發生這個錯誤。 下列其中一種或多種解決方案可能可以解決此問題：  
  
- 關閉 [原生相容性模式]  **** 和 [Managed 相容性模式] ****。  
  
- 在 Visual Studio 2013 中，關閉 [啟用原生編輯後繼續] ****。  
  
- 將兩部電腦重新開機。  
  
- 如果遠端偵錯要求輸入認證，請核取這個選項儲存認證。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)
