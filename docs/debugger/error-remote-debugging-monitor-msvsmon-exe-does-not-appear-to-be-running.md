---
description: 這個錯誤訊息表示 Visual Studio 無法在遠端電腦上找到正確的 Visual Studio 遠端偵錯監視執行個體。
title: Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c40e36548e17bbd4d37192364667a369bdcbb47
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146790"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。
這個錯誤訊息表示 Visual Studio 無法在遠端電腦上找到正確的 Visual Studio 遠端偵錯監視執行個體。 必須安裝 Visual Studio 遠端偵錯監視，才能執行遠端偵錯。 如需下載和設定遠端偵錯程式的詳細資訊，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

> [!IMPORTANT]
> 如果您認為因為產品錯誤而收到此訊息，請 [向 Visual Studio 報告這個問題](../ide/how-to-report-a-problem-with-visual-studio.md)。 如果您需要更多協助，請參閱 [Talk to Us](../ide/feedback-options.md) 與 Microsoft 連絡。

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>我在 Visual Studio 2010 或更早版本中偵錯時收到這則訊息
 如果您使用的 Visual Studio 版本是 Visual Studio 2010 或更早版本，在未啟用檔案或印表機共用時，也可能會收到這個錯誤。 若要深入了解這個問題，請參閱本文件的 Visual Studio 2010 版本：[Error: The Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) does not appear to be running on the remote computer. - Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100)) (錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。- Visual Studio 2010)

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>我在本機偵錯時收到這則訊息
 如果您是在本機偵錯時收到這則訊息，可能要歸責於您的防毒軟體或協力廠商防火牆。 Visual Studio 是 32 位元的應用程式，所以使用 64 位元版本的遠端偵錯工具偵錯 64 位元的應用程式。 這兩種處理序使用本機電腦內的區域網路進行通訊。 雖然沒有流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。

 下列章節會列出一些之所以可能收到這則訊息的其他原因，以及修正問題的可行作法。

## <a name="the-remote-machine-is-not-reachable"></a>找不到遠端電腦
 請嘗試 [ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) 遠端電腦。 如果它不回覆 ping，遠端工具將無法連線。 請嘗試重新啟動遠端電腦，另確定它的網路設定正確。

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>遠端偵錯工具的版本與 Visual Studio 版本不相符
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 請移至 [下載中心](https://www.microsoft.com/download) ，尋找正確的遠端偵錯工具版本。

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本機和遠端電腦的驗證模式不同
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))。

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>遠端偵錯工具在不同的使用者帳戶下執行
 您可以使用下列方式的其中之一解決這個問題：

- 您可以停止遠端偵錯工具，再以使用的本機電腦帳戶重新啟動它。

- 您可以從命令列使用 **/allow \<username>** 參數啟動遠端偵錯程式：`msvsmon /allow <username@computer>`

- 您可以將使用者新增至遠端偵錯工具的權限 (在遠端偵錯工具視窗：[工具] > [權限])。

- 如果無法使用前述步驟中的方法，您可以允許任何使用者執行遠端偵錯。 在遠端偵錯工具視窗中，移至 [工具] > [選項] 對話方塊。 當您選取 [無驗證]   時，可以接著選取 [允許任何使用者執行偵錯] 。 不過，您應該只有在沒有任何選擇或在私人網路上，才使用這個選項。

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>遠端電腦上的防火牆不允許連入連線至遠端偵錯工具
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

## <a name="anti-virus-software-is-blocking-the-connections"></a>防毒軟體封鎖連線
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊
 檢閱您的網路安全性確定它沒有封鎖通訊。 如需 Windows 網路安全性原則的詳細資訊，請參閱 [安全性原則設定](/windows/device-security/security-policy-settings/security-policy-settings)。

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>網路太忙碌無法支援遠端偵錯
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。

## <a name="more-help"></a>詳細的說明
 若要取得更多遠端偵錯程式說明（包括命令列參數），請按一下 [遠端偵錯程式] 視窗中的 [說明 **> 使用** 方式]。 如果您未開啟，您可以將下列程式程式碼複製到 [檔案  **瀏覽器** ] 視窗，以查看該網頁。  (您需要取代為 \<Visual Studio installation directory> Visual Studio 安裝的位置。 ) 

 res:// *\<Visual Studio installation directory>* \Common7\IDE\Remote% 20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
