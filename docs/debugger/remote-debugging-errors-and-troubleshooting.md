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
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043341"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>遠端偵錯錯誤和疑難排解

當您嘗試進行遠端偵錯時，您可能會遇到下列錯誤。

- [錯誤：無法自動逐步執行至伺服器](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [錯誤：遠端電腦未顯示於 [遠端連線] 對話方塊](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>系統管理員身分執行遠端偵錯工具

如果您沒有系統管理員身分執行遠端偵錯工具，您可能會遇到的問題。 例如，您可能會看到下列錯誤：「 Visual Studio 遠端偵錯工具 (MSVSMON。EXE) 有偵錯此處理序的權限不足。 」 如果您正在執行遠端偵錯工具為應用程式 （而非服務），您可能會看到[不同的使用者帳戶](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)時發生錯誤。

### <a name="when-running-the-remote-debugger-as-a-service"></a>當以服務方式執行遠端偵錯工具

當 s 服務方式執行遠端偵錯工具，我們建議系統管理員身分執行有幾個原因：

- 遠端偵錯工具服務僅允許連線系統管理員，因此會有**沒有**由系統管理員身分執行它導入新的安全性風險。

- 它可以防止 Visual Studio 使用者有更多的權限偵錯與遠端偵錯工具本身的處理序的結果沒有的錯誤。

- 若要簡化的安裝和設定遠端偵錯工具。

雖然您可以偵錯而以管理員身分執行遠端偵錯工具，正確地進行這項工作的幾項需求，它們通常需要更進階的服務設定步驟。

- 您在遠端電腦使用的帳戶必須擁有**服務方式登入**權限。 請參閱底下 「 若要新增登入為服務 」 的步驟[無法連線回](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)錯誤文章。

- 帳戶必須具有偵錯目標處理序的權限。 若要取得這些權限，您必須執行遠端偵錯工具相同的帳戶以進行偵錯處理程序。 （簡單的替代方法是以系統管理員身分執行服務）。 

- 帳戶必須能夠連線到 （也就是向） Visual Studio 電腦透過網路。 在網域中，很容易連接，如果內建本機系統或網路服務帳戶或網域帳戶下執行遠端偵錯工具。 內建的帳戶有更高的安全性權限，可以有安全性風險。

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>當應用程式 （一般模式） 執行遠端偵錯工具

如果您嘗試附加至您自己的非提高權限處理序 （例如，一般的應用程式），則並不重要，如果您系統管理員身分執行遠端偵錯工具。

您想要以數種案例中的系統管理員身分執行遠端偵錯工具：

- 您想要附加至另一個使用者身分執行的處理序 (例如當偵錯 IIS)，或

- 您嘗試啟動另一個處理序，並且您想要啟動的程序是系統管理員。

這麼做**未**想要以系統管理員身分執行，如果您想要啟動處理程序，而且您想要啟動的程序應該**不**是系統管理員。

## <a name="see-also"></a>另請參閱
- [Remote Debugging](../debugger/remote-debugging.md)