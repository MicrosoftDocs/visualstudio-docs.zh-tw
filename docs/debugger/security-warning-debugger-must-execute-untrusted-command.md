---
title: 安全性警告： 偵錯工具必須執行未受信任的命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4ab45feeae409a1951e1a57e964eaaa5963896
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690346"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Security Warning: Debugger Must Execute Untrusted Command
這個警告對話方塊會在您使用來源伺服器時出現。 它會指出，偵錯工具需要執行以取得原始程式碼的命令不在 srcsvr.ini 檔中所包含來源伺服器的受信任命令清單中。 如果這是有效的命令，您可將它加入至 srcsvr.ini 檔。 否則，您不應該執行該命令。 如需詳細資訊，請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="message-text"></a>訊息文字
 **偵錯工具必須執行下列未受信任的命令，才能從來源伺服器取得原始程式碼。**

 **如果偵錯符號檔 (\*.pdb) 不是來自已知且受信任的來源，這個命令可能無效，或者執行這個命令會帶來危險。**

 **要執行這個命令嗎?**

## <a name="uielement-list"></a>UIElement 清單
 文字 方塊中的.pdb 檔從要執行命令。

 執行可讓要執行的命令。

 不執行停止執行命令，並將檔案從來源伺服器的下載。

## <a name="see-also"></a>請參閱
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [偵錯工具安全性](../debugger/debugger-security.md)
- [來源伺服器](/windows/desktop/Debug/source-server-and-source-indexing)