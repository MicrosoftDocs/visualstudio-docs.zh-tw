---
title: 無法連接到 Microsoft 可視化工作室遠端調試監視器 |微軟文件
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
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
ms.openlocfilehash: d6173d6b3525a1bd723bc859d34b889b3796d295
ms.sourcegitcommit: c3b92a9912a5816f16c6059d1738dbc833851346
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81397372"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
由於遠端調試監視器未在遠端電腦上正確設置,或者由於網路問題或存在防火牆,無法訪問遠端電腦,因此可能會出現此消息。

> [!IMPORTANT]
> 如果您認為您因為產品錯誤而收到此訊息,請向 Visual Studio[報告此問題](../ide/how-to-report-a-problem-with-visual-studio.md)。 如果您需要更多協助，請參閱 [Talk to Us](../ide/feedback-options.md) 與 Microsoft 連絡。

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>什麼是詳細的錯誤消息?

消息`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor`是泛型的。 通常,錯誤字串中包含更具體的消息,這可以説明您確定問題的原因或搜索更精確的修復程式。 以下是一些附加在主錯誤訊息上的更常見錯誤訊息:

- [除錯器無法連接到遠端電腦。除錯器無法解析指定的電腦名稱](#cannot_connect)
- [遠端除錯器拒絕連線要求](#rejected)
- [與遠端終結點的連線已終止](#connection_terminated)
- [存取記憶體的不合法](#invalid_access)
- [遠端電腦上沒有按指定名稱執行的伺服器](#no_server)
- [要求的名稱有效,但找不到請求類型的資料](#valid_name)
- [目標電腦上的視覺化工作室遠端除錯器無法連線到此電腦](#cant_connect_back)
- [存取被拒](#access_denied)
- [發生安全性套件的錯誤](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>除錯器無法連接到遠端電腦。 除錯器無法解析指定的電腦名稱

請嘗試這些步驟：

1. 請確保在 **「附加到流程**」對話框或專案屬性(要設置屬性)中輸入有效的電腦名稱和埠號(要設置屬性,請參閱[這些步驟](#server_incorrect))。 電腦名稱必須具有以下格式:

    `computername:port`

    > [!NOTE]
    > 埠號必須與[遠端除錯器的連接埠號](../debugger/remote-debugger-port-assignments.md)匹配,遠端除錯器*必須在*目標電腦上運行。

2. 如果電腦名稱不起作用,請嘗試使用 IP 位址和埠號。

3. 確保在目標電腦上執行的遠端除錯器版本與您的 Visual Studio 版本匹配。 要取得遠端除錯器的正確版本,請參閱[遠端除錯](../debugger/remote-debugging.md)。

    > [!TIP]
    > 如果要附加到行程,但連線成功但看不到所需的行程,請**從所有使用者中選擇「顯示行程」複選框**。 如果您在不同的使用者帳戶下連接,這將顯示進程。

4. 如果這些步驟不能解決此錯誤,請參考[無法存取遠端電腦](#dns)。

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>遠端除錯器拒絕連線要求

在 **'附加到行程**'對話框或專案屬性中,請確保遠端電腦名稱和埠號與遠端除錯器視窗中顯示的名稱和埠號匹配。 如果不正確,請修復並重試。

如果這些值正確,並且消息提到 Windows**身份驗證**模式,請檢查遠端除錯器是否處於正確的身份驗證模式(**工具>選項**)。

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>與遠端終結點的連線已終止

如果要除錯 Azure 應用程式服務應用程式,請嘗試使用雲端資源管理員或伺服器資源管理程式中的[附加除錯器](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service),而不是**附加到行程**。

如果使用 **'附加到行程'** 來除錯:

- 在 **'附加到行程**'對話框或專案屬性中,請確保遠端電腦名稱和埠號與遠端除錯器視窗中顯示的名稱和埠號匹配。 如果不正確,請修復並重試。

- 如果嘗試使用主機名進行連接,請嘗試改用 IP 位址。

- 請查看伺服器上的應用程式日誌(Windows 上的事件查看器),以獲取更多詳細資訊以説明解決問題。

- 否則,請嘗試重新啟動具有管理員許可權的可視化工作室,然後重試。

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>存取記憶體的不合法

發生內部錯誤。 請重新啟動 Visual Studio 並再試一次。

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>遠端電腦上沒有按指定名稱執行的伺服器

可視化工作室無法連接到遠端調試器。 此消息可能由於以下幾個原因發生:

- 遠端調試器可能在不同的使用者帳戶下運行。 請參閱[以下步驟](#user_accounts)

- 埠在防火牆上被阻止。 確保防火牆[未阻止您的請求](#firewall),尤其是在使用第三方防火牆時。

- 遠端調試器版本與可視化工作室不匹配。 要取得遠端除錯器的正確版本,請參閱[遠端除錯](../debugger/remote-debugging.md)。

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>要求的名稱有效,但找不到請求類型的資料

遠端電腦存在,但 Visual Studio 無法連接到遠端除錯器。 此消息可能由於以下幾個原因發生:

- DNS 問題正在阻止連接。 請參閱[這些步驟](#dns)。

- 遠端調試器可能在不同的使用者帳戶下運行。 依[以下步驟操作](#user_accounts)。

- 埠在防火牆上被阻止。 確保防火牆[未阻止您的請求](#firewall),尤其是在使用第三方防火牆時。

- 遠端調試器版本與可視化工作室不匹配。 要取得遠端除錯器的正確版本,請參閱[遠端除錯](../debugger/remote-debugging.md)。

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>目標電腦上的視覺化工作室遠端除錯器無法連線到此電腦

遠端調試器可能在不同的使用者帳戶下運行。 在遠端除錯器中,打開 **「工具>將**使用者添加到遠端除錯器的權限的權限。 有關詳細資訊,請參閱[遠端除錯器正在其他使用者帳戶下執行](#user_accounts)。

如果錯誤消息還提到防火牆,則本地電腦上的防火牆可能阻止遠端電腦的通信回 Visual Studio。 請參閱[這些步驟](#firewall)。

## <a name="access-denied"></a><a name="access_denied"></a>存取被拒

如果您嘗試從 32 位元電腦(不支援)在 64 位元遠端電腦上調試,則可能會看到此錯誤。

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>發生安全性套件的錯誤

這可能是特定於 Windows XP 和 Windows 7 的舊問題。 請參考[此資訊](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)。

## <a name="causes-and-recommendations"></a>原因和建議

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>無法存取遠端電腦

如果無法使用遠端電腦名稱進行連接,請嘗試改用 IP 位址。 您可以在`ipconfig`遠端電腦上的命令列中使用獲取 IPv4 位址。 如果使用 HOSTS 檔,請驗證該檔配置是否正確。

如果失敗,請驗證遠端電腦在網路上是否可以訪問[(ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10))遠程電腦)。 不支援透過 Internet 進行遠端調試,但在某些 Microsoft Azure 方案中除外。

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>伺服器名稱不正確或第三方軟體干擾遠端除錯器

在 Visual Studio 中,查看專案屬性並確保伺服器名稱正確。 請參閱[C# 和可視化基礎](../debugger/remote-debugging-csharp.md#remote_csharp)和[C++](../debugger/remote-debugging-cpp.md#remote_cplusplus)的主題。 對 ASP.NET,根據項目類型開啟**屬性/Web /伺服器**或**屬性/除錯**。

> [!NOTE]
> 如果要附加到進程,則不使用專案屬性中的遠端設置。

如果伺服器名稱正確,則防病毒軟體或第三方防火牆可能阻止遠端調試器。 在本地調試時,可能會發生這種情況,因為 Visual Studio 是一個 32 位元應用程式,因此它使用 64 位元版本的遠端調試器來調試 64 位元應用程式。 32 位元和 64 位元程序使用本地電腦中的本地網路進行通信。 雖然沒有網路流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>遠端除錯器在不同的使用者帳戶下執行

默認情況下,遠端調試器將僅接受來自啟動遠端調試器的使用者和管理員組成員的連接。 必須顯式授予其他用戶許可權。

您可以使用下列方式的其中之一解決這個問題：

- 將 Visual Studio 使用者添加到遠端除錯器的許可權(在遠端除錯器視窗中,選擇**工具>許可權**)。

- 在遠端電腦上,在 Visual Studio 電腦上使用的使用者帳戶和密碼下重新啟動遠端調試器。

    > [!NOTE]
    > 如果在遠端伺服器上運行遠端除錯器,請右鍵單擊遠端除錯器應用並選擇 **「作為管理員執行**」(或者,可以將遠端除錯器作為服務運行)。 如果您沒有在遠端伺服器上運行它,只需正常啟動它。

- 您可以從命令列使用 **/allow \<使用者名稱>** 參數：`msvsmon /allow <username@computer>` 啟動遠端偵錯工具。

- 或者,您可以允許任何使用者執行遠端除錯。 在遠端偵錯工具視窗中，移至 [工具] > [選項]**** 對話方塊。 當您選取 [無驗證]   **** 時，可以接著選取 [允許任何使用者執行偵錯] ****。 但是,僅當其他選項失敗或處於專用網路時,才應嘗試此選項。

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>遠端電腦上的防火牆不允許連接到遠端除錯器
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>遠端偵錯工具的版本與 Visual Studio 版本不相符
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 要取得遠端除錯器的正確版本,請參閱[遠端除錯](../debugger/remote-debugging.md)。

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本機和遠端電腦的驗證模式不同
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 您可以更改身份驗證模式。 在遠端除錯器視窗中,轉到 **「工具>選項」** 對話框。

 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))。

### <a name="anti-virus-software-is-blocking-the-connections"></a>防毒軟體封鎖連線
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊
 檢閱您的網路安全性確定它沒有封鎖通訊。 有關 Windows 網路安全原則的詳細資訊,請參閱[安全原則設定](/windows/device-security/security-policy-settings/security-policy-settings)。

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>網路太忙碌無法支援遠端偵錯
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。

## <a name="more-help"></a>詳細的說明
 要獲得更多遠端除錯器説明,打開遠端除錯器的幫助頁(**説明>** 遠端除錯器中的使用方式)。

## <a name="see-also"></a>另請參閱
- [遠端除錯](../debugger/remote-debugging.md)
