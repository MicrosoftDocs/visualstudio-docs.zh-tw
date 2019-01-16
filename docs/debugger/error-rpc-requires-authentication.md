---
title: 錯誤：RPC 需要驗證 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f319ba24a52a99994e693774aa9e7c0db7757e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874403"
---
# <a name="error-rpc-requires-authentication"></a>錯誤：RPC 需要驗證
Visual Studio 偵錯工具無法連接至遠端電腦。 本機電腦上啟用了 RPC 原則，會阻止遠端偵錯進行。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  執行`\` *windir*`\system32\regedt32.exe`  
  
2.  找出並刪除`HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`。  
  
3.  重新啟動您的電腦，如此登錄變更才會生效。  
  
4.  如果問題持續發生，請連絡您的網域系統管理員的相關**電腦設定 > 系統管理範本 > System > 遠端程序呼叫 > 未驗證的 RPC 用戶端的限制**群組原則設定。