---
title: "錯誤： RPC 需要驗證 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3431ee286787d99e8601fbed7cad3012ffcaf68e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="error-rpc-requires-authentication"></a>錯誤：RPC 需要驗證
Visual Studio 偵錯工具無法連接至遠端電腦。 本機電腦上啟用了 RPC 原則，會阻止遠端偵錯進行。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  執行`\` *windir*`\system32\regedt32.exe`  
  
2.  找出並刪除`HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`。  
  
3.  重新啟動您的電腦，如此登錄變更才會生效。  
  
4.  如果問題持續發生，請洽詢網域管理員有關**電腦設定 > 系統管理範本 > System > 遠端程序呼叫 > 未經驗證的 RPC 用戶端的限制**群組原則設定。