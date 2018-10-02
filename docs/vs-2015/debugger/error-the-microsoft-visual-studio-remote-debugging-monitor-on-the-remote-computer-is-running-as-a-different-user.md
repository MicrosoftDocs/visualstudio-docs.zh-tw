---
title: 錯誤： Microsoft Visual Studio 遠端偵錯監視遠端電腦上執行不同的使用者身分 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5256feb22e09eb75fa8f4d5a50e8beafeec8f97d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491100"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視以不同使用者執行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[錯誤： Microsoft Visual Studio 遠端偵錯監視遠端電腦上執行不同的使用者身分](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user)。  
  
您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：  
  
 遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視，目前是以不同的使用者身分在執行。  
  
## <a name="cause"></a>原因  
 當您以 [非驗證] 模式進行偵錯，但啟動 msvsmon 的使用者不是執行 Visual Studio 的使用者時，就會出現這個訊息。  
  
## <a name="solution"></a>方案  
 最安全且最理想的方案就是以相同的使用者帳戶執行遠端偵錯監視 (msvsmon.exe) 和 Visual Studio。 如果您不能這麼做，您可以與其他帳戶下執行遠端偵錯監視**允許任何使用者執行偵錯**中遠端偵錯監視 選項**選項** 對話方塊。  
  
> [!CAUTION]
>  將進行連接的權限授與其他使用者，可能會意外連接至錯誤的遠端偵錯工作階段。 在中偵錯**不需要驗證**模式非常不安全，應該謹慎使用。  
  
 如需詳細資訊，請參閱 <<c0> [ 啟動遠端偵錯監視](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c)。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)



