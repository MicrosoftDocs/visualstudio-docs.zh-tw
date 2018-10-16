---
title: 錯誤： Microsoft Visual Studio 遠端偵錯監視遠端電腦上沒有連線到此電腦的權限 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
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
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c65a5ed9cc06c8d9c4d471b878762d863802f5f0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289031"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視沒有連接至這部電腦的使用權限
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當嘗試執行 Visual Studio 遠端偵錯監視 (msvsmon) 的使用者沒有本機電腦上的帳戶時，就會發生這個錯誤。  
  
### <a name="to-fix-this-problem"></a>若要修復這個問題  
  
-   使用與在遠端電腦上執行 msvsmon 的使用者帳戶相同的名稱和密碼，將使用者帳戶加入到 Visual Studio 偵錯工具主機電腦。  
  
     \-或-  
  
-   將 msvsmon 當成具有使用權限呼叫本機電腦的使用者來執行。 這表示這個使用者必須是 msvsmon 電腦上的網域使用者和系統管理員。 您可以下列兩種方式的其中一種，指定執行 msvsmon 的使用者帳戶：  
  
    -   以滑鼠右鍵按一下 msvsmon 圖示，然後選擇 **執行身分**快顯功能表  
  
     \-或-  
  
    -   在命令提示字元中，執行 `runas.exe`。  
  
## <a name="see-also"></a>另請參閱  
 [跨網域遠端偵錯](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



