---
title: 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03e4ef05c1615e7798cd111f9cc5f95976abeebc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871321"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視以不同使用者執行
您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：

 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行。

## <a name="cause"></a>原因
 當您以 [非驗證] 模式進行偵錯，但啟動 msvsmon 的使用者不是執行 Visual Studio 的使用者時，就會出現這個訊息。

## <a name="solution"></a>解決方案
 最安全且最理想的方案就是以相同的使用者帳戶執行遠端偵錯監視 (msvsmon.exe) 和 Visual Studio。 如果無法這麼做的話，您可以使用其他帳戶執行遠端偵錯監視，方法是在遠端偵錯監視的 [選項] 對話方塊中選取 [允許任何使用者執行偵錯] 選項。

> [!CAUTION]
> 將進行連接的權限授與其他使用者，可能會意外連接至錯誤的遠端偵錯工作階段。 以 [非驗證] 模式進行偵錯非常不安全，請務必小心使用。

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [遠端偵錯](../debugger/remote-debugging.md)