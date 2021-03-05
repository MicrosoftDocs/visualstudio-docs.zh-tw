---
description: Visual Studio 偵錯工具無法連接至遠端電腦。
title: RPC 需要驗證 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f22998bc1c71a242b985739b2b92ba9743535d83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146713"
---
# <a name="error-rpc-requires-authentication"></a>錯誤：RPC 需要驗證
Visual Studio 偵錯工具無法連接至遠端電腦。 本機電腦上啟用了 RPC 原則，會阻止遠端偵錯進行。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 執行 `\` *windir*`\system32\regedt32.exe`

2. 找出並刪除 `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` 。

3. 重新啟動您的電腦，如此登錄變更才會生效。

4. 如果問題持續發生，請洽詢您的網域系統管理員，瞭解 **電腦設定 > 系統管理範本 > 系統 > 遠端程序呼叫 > 限制未驗證的 RPC 用戶端** 群組原則設定。
