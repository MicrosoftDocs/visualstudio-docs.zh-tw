---
title: 錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607369b4b10a98e9464a0ede15e2f9dce5fac5a9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399153"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行
您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：

 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行。

## <a name="cause"></a>原因
 當您以 [非驗證] 模式進行偵錯，但啟動 msvsmon 的使用者不是執行 Visual Studio 的使用者時，就會出現這個訊息。

## <a name="solution"></a>方案
 最安全且最理想的方案就是以相同的使用者帳戶執行遠端偵錯監視 (msvsmon.exe) 和 Visual Studio。 如果無法這麼做的話，您可以使用其他帳戶執行遠端偵錯監視，方法是在遠端偵錯監視的 [選項] 對話方塊中選取 [允許任何使用者執行偵錯] 選項。

> [!CAUTION]
> 將進行連接的權限授與其他使用者，可能會意外連接至錯誤的遠端偵錯工作階段。 以 [非驗證] 模式進行偵錯非常不安全，請務必小心使用。

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)