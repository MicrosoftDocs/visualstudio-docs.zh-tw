---
title: 錯誤：RPC 需要驗證 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102727"
---
# <a name="error-rpc-requires-authentication"></a>錯誤：RPC 需要驗證
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 偵錯工具無法連接至遠端電腦。 本機電腦上啟用了 RPC 原則，會阻止遠端偵錯進行。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 執行`\` *windir*`\system32\regedt32.exe`  
  
2. 找出並刪除`HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`。  
  
3. 重新啟動您的電腦，如此登錄變更才會生效。  
  
4. 如果問題持續發生，請連絡您的網域系統管理員的相關**電腦設定-> 系統管理範本-> 系統-> 遠端程序呼叫-> 未經驗證的 RPC 用戶端的限制**群組原則設定。
