---
title: 錯誤： Microsoft Visual Studio 遠端偵錯監視遠端電腦上執行不同的使用者身分 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2bdc731b65a8d451b6882914e8bed1abca2139b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視以不同使用者執行
您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：  
  
 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行。  
  
## <a name="cause"></a>原因  
 當您以 [非驗證] 模式進行偵錯，但啟動 msvsmon 的使用者不是執行 Visual Studio 的使用者時，就會出現這個訊息。  
  
## <a name="solution"></a>方案  
 最安全且最理想的方案就是以相同的使用者帳戶執行遠端偵錯監視 (msvsmon.exe) 和 Visual Studio。 如果您無法這樣做，請您就可以使用其他帳戶下執行遠端偵錯監視**允許任何使用者執行偵錯**選取遠端偵錯監視選項**選項** 對話方塊。  
  
> [!CAUTION]
>  將進行連接的權限授與其他使用者，可能會意外連接至錯誤的遠端偵錯工作階段。 中的偵錯**非驗證**模式非常不安全，應該謹慎使用。
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)