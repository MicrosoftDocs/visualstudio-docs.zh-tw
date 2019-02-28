---
title: '錯誤: Kerberos 驗證失敗，|Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb327ad703c744f94970162f493cb61dffb8fac3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701065"
---
# <a name="error-kerberos-authentication-failed"></a>錯誤：Kerberos 驗證失敗
當您嘗試進行遠端偵錯時，可能會看到下列錯誤訊息：

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 當 Visual Studio 遠端偵錯監視是使用本機系統或網路服務帳戶執行時，就會發生這個錯誤。 在其中一個帳戶下，遠端偵錯工具必須建立 Kerberos 驗證連接，以與 Visual Studio 偵錯工具主機電腦通訊。

 Kerberos 驗證在下列情況下無法使用：

- 目標電腦或者是偵錯工具主機電腦位於工作群組中，而非網域中。

   \-或-

- 在網域控制站上已停用 Kerberos。

  如果無法使用 Kerberos 驗證，請將帳戶變更為用於執行 Visual Studio 遠端偵錯監視的帳戶。 程序，請參閱[錯誤： 目標電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)。

  如果兩部電腦都連接至相同的網域，而您仍然收到這個訊息，請確認目標電腦上的 DNS 有正確解析偵錯工具主機電腦的名稱。 請參閱下列程序。

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>若要確認目標電腦上的 DNS 有正確解析偵錯工具主機電腦的名稱

1.  在目標電腦上，開啟 [開始] 功能表，指向 [附屬應用程式]，然後按一下 [命令提示字元]。

2.  在 [命令提示字元] 視窗中，鍵入：

    ```cmd
    ping <debugger_host_computer_name>
    ```

3.  `ping` 回應的第一行顯示針對指定電腦，DNS 所傳回的電腦全名和 IP 位址。

4.  在偵錯工具主機電腦上，開啟 [命令提示字元] 視窗，並執行 `ipconfig`。

5.  比較 IP 位址值。

## <a name="see-also"></a>請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
