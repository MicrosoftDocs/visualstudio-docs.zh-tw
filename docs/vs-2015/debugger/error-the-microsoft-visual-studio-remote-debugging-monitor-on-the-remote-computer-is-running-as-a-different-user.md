---
title: 錯誤：Microsoft Visual Studio 遠端偵錯監視遠端電腦上執行不同的使用者身分 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7cba3de8aa07a021d61e1ebb2a2c97f568eaf9ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388428"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：  
  
 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行。  
  
## <a name="cause"></a>原因  
 當您以 [非驗證] 模式進行偵錯，但啟動 msvsmon 的使用者不是執行 Visual Studio 的使用者時，就會出現這個訊息。  
  
## <a name="solution"></a>方案  
 最安全且最理想的方案就是以相同的使用者帳戶執行遠端偵錯監視 (msvsmon.exe) 和 Visual Studio。 如果無法這麼做的話，您可以使用其他帳戶執行遠端偵錯監視，方法是在遠端偵錯監視的 [選項] 對話方塊中選取 [允許任何使用者執行偵錯] 選項。  
  
> [!CAUTION]
> 將進行連接的權限授與其他使用者，可能會意外連接至錯誤的遠端偵錯工作階段。 以 [非驗證] 模式進行偵錯非常不安全，請務必小心使用。  
  
 如需詳細資訊，請參閱 <<c0> [ 啟動遠端偵錯監視](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c)。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
