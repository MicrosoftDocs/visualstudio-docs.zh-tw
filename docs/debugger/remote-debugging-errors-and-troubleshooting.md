---
title: 遠端偵錯錯誤和故障排除 |微軟文檔
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
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302088"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>遠端偵錯錯誤和疑難排解

嘗試遠端偵錯時，可能會遇到以下錯誤。

- [錯誤：無法自動踏入伺服器](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [無法連接到 Microsoft 視覺化工作室遠端偵錯監視器](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [錯誤：遠端電腦未顯示於 [遠端連線] 對話方塊](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>以管理員身份運行遠端偵錯器

如果不以管理員身份運行遠端偵錯器，則可能會遇到問題。 例如，您可能會看到以下錯誤："視覺化工作室遠端偵錯器 （MSVSMON）。EXE） 沒有足夠的許可權來調試此過程。 如果將遠端偵錯器作為應用程式（而不是服務）運行，您可能會看到[不同的使用者帳戶](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)錯誤。

### <a name="when-running-the-remote-debugger-as-a-service"></a>將遠端偵錯器作為服務運行時

將遠端偵錯器作為服務運行時，我們建議將其作為管理員運行，原因如下：

- 遠端偵錯器服務僅允許來自管理員的連接，因此沒有**引入新的安全風險**，通過作為管理員運行它。

- 當 Visual Studio 使用者比遠端偵錯器本身擁有更多調試進程的許可權時，它可以防止導致錯誤。

- 簡化遠端偵錯器的設置和配置。

雖然無需作為管理員運行遠端偵錯器即可進行調試，但有幾個要求使此調試正常工作，並且通常需要更高級的服務配置步驟。

- 您在遠端電腦上使用的帳戶必須具有**登錄作為服務**許可權。 請參閱[無法連接回](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)錯誤文章中的"將登錄作為服務添加登錄"下的步驟。

- 帳戶必須具有調試目標進程的許可權。 要獲得這些許可權，必須在與要調試的進程相同的帳戶下運行遠端偵錯器。 （更簡單的替代方法是以管理員身份運行服務。 

- 帳戶必須能夠通過網路連接到 Visual Studio 電腦（即使用身份驗證）。 在域上，如果遠端偵錯器在內置本地系統或網路服務帳戶或域帳戶下運行，則更容易連接。 內置帳戶具有更高的安全許可權，可能會帶來安全風險。

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>當作為應用程式運行遠端偵錯器時（正常模式）

如果您嘗試附加到自己的非提升進程（如普通應用程式），則是否以管理員身份運行遠端偵錯器並不重要。

您希望在以下幾個方案中以管理員身份運行遠端偵錯器：

- 您希望附加到以其他使用者身份運行的進程（例如調試 IIS 時），或

- 您正在嘗試啟動另一個進程，並且要啟動的過程是管理員。

如果要啟動進程 **，則不想**以管理員身份運行，並且要啟動的進程**不應**是管理員。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)