---
title: 嘗試聯繫遠端電腦時，發生 DCOM 錯誤。 存取被拒絕。 | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cabac4997480b626714c129daef0511643ae2a50
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497965"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>嘗試聯繫遠端電腦時，發生 DCOM 錯誤。 存取被拒絕。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新版本位於[嘗試聯繫遠端電腦時，發生 DCOM 錯誤。存取遭到拒絕。](https://docs.microsoft.com/visualstudio/debugger/a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied).  
  
在下列情況下，遠端偵錯會使用 DCOM 在本機與遠端電腦之間進行通訊：  
  
-   偵錯工具已設定為 [原生相容性模式]  ，或是在 [工具]/[選項]/[偵錯]  頁面中核取了 [Managed 相容性模式]  。  
  
-   您正在偵錯 Managed C++ (C++/CLI) 程式碼。  
  
-   在 Visual Studio 2013 中，於 [工具]/[選項]/[偵錯]  頁面中核取了 [啟用原生編輯後繼續]  時。  
  
-   某些協力廠商偵錯情節  
  
 Visual Studio 處理序無法透過 DCOM 對遠端偵錯工具處理序進行自我驗證 (或認為提供的認證不足) 時，就會發生這個錯誤。 下列其中一種或多種解決方案可能可以解決此問題：  
  
-   關閉 [原生相容性模式]   和 [Managed 相容性模式] 。  
  
-   在 Visual Studio 2013 中，關閉 [啟用原生編輯後繼續] 。  
  
-   將兩部電腦重新開機。  
  
-   如果遠端偵錯要求輸入認證，請核取這個選項儲存認證。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)



