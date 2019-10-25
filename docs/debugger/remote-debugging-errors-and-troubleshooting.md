---
title: 遠端偵錯錯誤和疑難排解 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f41292c22de1d9c76007ca44cb7accbf82359b3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730024"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>遠端偵錯錯誤和疑難排解

當您嘗試從遠端進行調試時，可能會遇到下列錯誤。

- [Error: Unable to Automatically Step Into the Server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [錯誤：遠端電腦未顯示於 [遠端連線] 對話方塊](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>以系統管理員身分執行遠端偵錯程式

如果您不是以系統管理員身分執行遠端偵錯程式，可能會遇到問題。 例如，您可能會看到下列錯誤：「Visual Studio 遠端偵錯工具（MSVSMON。EXE）沒有足夠的許可權可進行此進程的偵錯工具。」 如果您是以應用程式（而非服務）執行遠端偵錯程式，您可能會看到[不同的使用者帳戶](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)錯誤。

### <a name="when-running-the-remote-debugger-as-a-service"></a>以服務方式執行遠端偵錯程式時

當以 s 服務的形式執行遠端偵錯程式時，我們建議您以系統管理員身分執行它，原因如下：

- 遠端偵錯程式服務只允許來自系統管理員的連線，因此以管理員身分執行時，不會產生**任何**新的安全性風險。

- 它可以防止當 Visual Studio 使用者擁有比遠端偵錯程式本身更多的許可權來比對進程時，所造成的錯誤。

- 簡化遠端偵錯程式的安裝和設定。

雖然您不需要以系統管理員身分執行遠端偵錯程式，但有幾項需求可以正確運作，而且通常需要更多的服務設定步驟。

- 您在遠端電腦上使用的帳戶必須具有 [**以服務方式登**入] 許可權。 請參閱「[無法連線](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)到錯誤」文章中的「新增登入為服務」底下的步驟。

- 此帳戶必須具有偵錯工具目標進程的許可權。 若要取得這些許可權，您必須在與要進行調試的進程相同的帳戶下執行遠端偵錯程式。 （較簡單的替代方法是以系統管理員身分執行服務）。 

- 帳戶必須能夠透過網路連線回到（也就是驗證） Visual Studio 的電腦。 在網域上，如果遠端偵錯程式是在內建的本機系統或網路服務帳戶或網域帳戶之下執行，則可以更輕鬆地重新連接。 內建帳戶具有更高的安全性許可權，可能會帶來安全性風險。

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>以應用程式的形式執行遠端偵錯程式時（正常模式）

如果您嘗試附加至您自己的未提高許可權進程（例如一般應用程式），您是否以系統管理員身分執行遠端偵錯程式並不重要。

您想要在數個案例中，以系統管理員身分執行遠端偵錯程式：

- 您想要附加至以另一位使用者身分執行的進程（例如，在偵錯工具時），或

- 您嘗試啟動另一個進程，而您想要啟動的進程是系統管理員。

如果您想要啟動處理常式，而您想要啟動的進程**不應為**系統管理員，您就**不**需要以系統管理員身分執行。

## <a name="see-also"></a>請參閱
- [Remote Debugging](../debugger/remote-debugging.md)