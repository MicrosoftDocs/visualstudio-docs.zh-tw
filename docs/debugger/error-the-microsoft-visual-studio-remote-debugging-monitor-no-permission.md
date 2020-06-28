---
title: 錯誤-遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視沒有連接到這部電腦的許可權
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9304c999abb1401af8e524551a999556826062
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460452"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>錯誤：遠端電腦上的 Microsoft Visual Studio 遠端偵錯監視沒有連接至這部電腦的使用權限

當嘗試執行 Visual Studio 遠端偵錯監視 (msvsmon) 的使用者沒有本機電腦上的帳戶時，就會發生這個錯誤。 使用舊版的調試引擎進行遠端偵錯時，可能會發生此錯誤。

## <a name="to-fix-this-problem"></a>若要修復這個問題

- 使用與在遠端電腦上執行 msvsmon 的使用者帳戶相同的名稱和密碼，將使用者帳戶加入到 Visual Studio 偵錯工具主機電腦。

   \- 或 -

- 將 msvsmon 當成具有使用權限呼叫本機電腦的使用者來執行。 這表示這個使用者必須是 msvsmon 電腦上的網域使用者和系統管理員。 您可以下列兩種方式的其中一種，指定執行 msvsmon 的使用者帳戶：

  - 以滑鼠右鍵按一下 msvsmon 圖示，並從捷徑功能表中選擇 [執行身分]****

    \- 或 -

  - 在命令提示字元中，執行 `runas.exe`。

## <a name="see-also"></a>另請參閱

- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [遠端偵錯](../debugger/remote-debugging.md)