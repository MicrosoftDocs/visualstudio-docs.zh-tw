---
title: 嘗試聯繫遠端電腦時，發生 DCOM 錯誤。 存取被拒絕。 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a46129dd8b83cfbbdb62c6118cb2575b1b8cfc8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>嘗試聯繫遠端電腦時，發生 DCOM 錯誤。 存取被拒絕。
在下列情況下，遠端偵錯會使用 DCOM 在本機與遠端電腦之間進行通訊：  
  
-   偵錯工具設定為**原生相容性模式**或**Managed 相容性模式**簽入**工具 > 選項 > 偵錯**頁面  
  
-   您正在偵錯 Managed C++ (C++/CLI) 程式碼。  
  
-   在 Visual Studio 2013 中，當**啟用原生編輯後繼續**簽入**工具 > 選項 > 偵錯**頁面  
  
-   某些協力廠商偵錯情節  
  
 Visual Studio 處理序無法透過 DCOM 對遠端偵錯工具處理序進行自我驗證 (或認為提供的認證不足) 時，就會發生這個錯誤。 下列其中一種或多種解決方案可能可以解決此問題：  
  
-   關閉 [原生相容性模式]   和 [Managed 相容性模式] 。  
  
-   在 Visual Studio 2013 中，關閉 [啟用原生編輯後繼續] 。  
  
-   將兩部電腦重新開機。  
  
-   如果遠端偵錯要求輸入認證，請核取這個選項儲存認證。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)