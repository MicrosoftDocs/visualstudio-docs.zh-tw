---
title: "錯誤： 無法連接至電腦&lt;名稱&gt;。 在網路上找不到電腦。 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ed30ca3baeb29f92c4d5f02b64c581ef9a37a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>錯誤： 無法連接至電腦&lt;名稱&gt;。 在網路上找不到電腦。
如果下列其中一種情況為 true 時，就會發生這個行為：  
  
-   與遠端電腦的連線中斷。  
  
-   在遠端電腦上的使用者帳戶已停用。  
  
-   遠端電腦上的密碼已到期。  
  
### <a name="to-resolve-this-behavior"></a>若要解決這個行為  
  
-   請確定本機電腦與遠端電腦位於相同的網路上。 方法是，使用 Microsoft Windows [檔案總管] (或 [檔案總管]) 嘗試存取遠端電腦。  
  
     -和-  
  
-   請確定已啟用您用以連接遠端電腦的使用者帳戶。  
  
     -和-  
  
-   請確定您用以連接遠端電腦的密碼是有效的，而且尚未到期。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯](../debugger/remote-debugging.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)