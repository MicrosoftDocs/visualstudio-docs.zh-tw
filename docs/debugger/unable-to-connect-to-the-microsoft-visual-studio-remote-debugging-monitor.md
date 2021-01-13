---
title: Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
description: 瞭解「無法連線至 Microsoft Visual Studio 遠端偵錯監視」的意義、可能的原因和解決方案。
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: dc34a5f58f8bc3c47526cc8ba8516311e94f0631
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150830"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
此訊息可能是因為遠端電腦上的遠端偵錯程式未正確設定，或遠端電腦因為網路問題或防火牆的存在而無法存取而發生。

> [!IMPORTANT]
> 如果您認為因為產品錯誤而收到此訊息，請將 [此問題](../ide/how-to-report-a-problem-with-visual-studio.md) 回報給 Visual Studio。 如果您需要更多協助，請參閱 [Talk to Us](../ide/feedback-options.md) 與 Microsoft 連絡。

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>詳細的錯誤訊息為何？

此 `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` 訊息為泛型。 通常，錯誤字串中會包含更明確的訊息，並可協助您找出問題的原因，或搜尋更精確的修正程式。 以下是幾個較常見的錯誤訊息，這些訊息會附加至主要錯誤訊息：

- [偵錯工具無法連接到遠端電腦。偵錯工具無法解析指定的電腦名稱稱](#cannot_connect)
- [遠端偵錯程式拒絕連接要求](#rejected)
- [已終止與遠端端點的連接](#connection_terminated)
- [記憶體位置的存取無效](#invalid_access)
- [遠端電腦上沒有執行指定名稱的伺服器](#no_server)
- [要求的名稱有效，但是找不到要求類型的資料](#valid_name)
- [目的電腦上的 Visual Studio 遠端偵錯工具無法連回這部電腦](#cant_connect_back)
- [拒絕存取](#access_denied)
- [發生安全性封裝特定的錯誤](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> 偵錯工具無法連接到遠端電腦。 偵錯工具無法解析指定的電腦名稱稱

請嘗試這些步驟：

1. 請確定您在 [ **附加至進程** ] 對話方塊中輸入有效的電腦名稱稱和埠號碼，或在 [專案屬性] (設定屬性時，請參閱 [下列步驟](#server_incorrect)) 。 電腦名稱稱必須是下列格式：

    `computername:port`

    > [!NOTE]
    > 埠號碼必須符合 *必須* 在目的電腦上執行之 [遠端偵錯程式的埠號碼](../debugger/remote-debugger-port-assignments.md)。

2. 如果電腦名稱稱無法運作，請改為嘗試 IP 位址和埠號碼。

3. 確定目的電腦上執行的遠端偵錯程式版本符合您 Visual Studio 的版本。 若要取得正確的遠端偵錯程式版本，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

    > [!TIP]
    > 如果您要附加至處理常式，並成功連接但沒有看到您想要的進程，請選取 [ **顯示所有使用者的進程] 核取方塊**。 如果您是在不同的使用者帳戶下連接，則會顯示處理常式。

4. 如果這些步驟無法解決此錯誤，請參閱 [無法連線到遠端電腦](#dns)。

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> 遠端偵錯程式拒絕連接要求

在 [ **附加至進程** ] 對話方塊或 [專案屬性] 中，確定 [遠端電腦名稱稱] 和 [埠號碼] 符合 [遠端偵錯程式] 視窗中顯示的名稱和埠號碼。 如果不正確，請修正後再試一次。

如果這些值正確，且訊息提及 **Windows 驗證** 模式，請檢查遠端偵錯程式是否處於正確的驗證模式 (**工具 > 選項**) 。

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> 已終止與遠端端點的連接

如果您正在進行 Azure App Service 應用程式的偵錯工具，請嘗試從 Cloud Explorer 或伺服器總管（而不是 **附加至進程**）使用 [[附加偵錯工具](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service)] 命令。

如果您使用 **附加至進程** 以進行偵錯工具：

- 在 [ **附加至進程** ] 對話方塊或 [專案屬性] 中，確定 [遠端電腦名稱稱] 和 [埠號碼] 符合 [遠端偵錯程式] 視窗中顯示的名稱和埠號碼。 如果不正確，請修正後再試一次。

- 如果您嘗試使用主機名稱進行連接，請嘗試改用 IP 位址。

- 檢查伺服器上的應用程式記錄檔 (事件檢視器 Windows) ，以取得有助於解決問題的詳細資訊。

- 否則，請嘗試以系統管理員許可權重新開機 Visual Studio，然後再試一次。

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> 記憶體位置的存取無效

發生內部錯誤。 請重新啟動 Visual Studio 並再試一次。

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> 遠端電腦上沒有執行指定名稱的伺服器

Visual Studio 無法連接到遠端偵錯程式。 此訊息可能有數種原因：

- 遠端偵錯程式可能在不同的使用者帳戶下執行。 請參閱 [下列步驟](#user_accounts)

- 防火牆上的埠遭到封鎖。 請確定防火牆不會 [封鎖您的要求](#firewall)，尤其是當您使用協力廠商防火牆時。

- 遠端偵錯程式版本與 Visual Studio 不相符。 若要取得正確的遠端偵錯程式版本，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> 要求的名稱有效，但是找不到要求類型的資料

遠端電腦存在，但是 Visual Studio 無法連接到遠端偵錯程式。 此訊息可能有數種原因：

- DNS 問題導致無法連線。 請參閱 [下列步驟](#dns)。

- 遠端偵錯程式可能在不同的使用者帳戶下執行。 請遵循下列 [步驟](#user_accounts)。

- 防火牆上的埠遭到封鎖。 請確定防火牆不會 [封鎖您的要求](#firewall)，尤其是當您使用協力廠商防火牆時。

- 遠端偵錯程式版本與 Visual Studio 不相符。 若要取得正確的遠端偵錯程式版本，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a> 目的電腦上的 Visual Studio 遠端偵錯工具無法連回這部電腦

遠端偵錯程式可能在不同的使用者帳戶下執行。 在遠端偵錯程式中，開啟 [ **工具] > 許可權** ，以將使用者加入遠端偵錯程式的許可權。 如需詳細資訊，請參閱 [使用不同的使用者帳戶執行遠端偵錯程式](#user_accounts)。

如果錯誤訊息也會提及防火牆，則本機電腦上的防火牆可能會阻止遠端電腦的通訊回到 Visual Studio。 請參閱 [下列步驟](#firewall)。

## <a name="access-denied"></a><a name="access_denied"></a> 拒絕存取

如果您嘗試從32位電腦上的64位遠端電腦上進行 debug 錯，您可能會看到此錯誤 (不支援) 。

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> 發生安全性封裝特定的錯誤

這可能是 Windows XP 和 Windows 7 特有的舊版問題。 請參閱此 [資訊](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)。

## <a name="causes-and-recommendations"></a>原因和建議

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> 無法連線到遠端電腦

如果您無法使用遠端電腦名稱稱進行連接，請嘗試改為使用 IP 位址。 您可以 `ipconfig` 在遠端電腦上的命令列中使用，以取得 IPv4 位址。 如果您使用 HOSTS 檔案，請確認它已正確設定。

如果失敗，請確認網路上的遠端電腦可以存取 ([偵測](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) 遠端電腦) 。 除非在某些 Microsoft Azure 案例中，否則不支援透過網際網路進行遠端偵錯。

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> 伺服器名稱不正確，或協力廠商軟體干擾遠端偵錯程式

在 Visual Studio 中，查看專案屬性，並確定伺服器名稱正確無誤。 請參閱 [c # 和 Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) 和 [c + +](../debugger/remote-debugging-cpp.md#remote_cplusplus)的主題。 針對 ASP.NET，請根據您的專案類型開啟 [ **屬性]/[Web/伺服器** ] 或 [ **屬性]/[調試** 程式]

> [!NOTE]
> 如果您要附加至處理常式，則不會使用專案屬性中的遠端設定。

如果伺服器名稱正確，您的防毒軟體或協力廠商防火牆可能會封鎖遠端偵錯程式。 在本機上進行偵錯工具時，可能會發生這種情況，因為 Visual Studio 是32位應用程式，所以它會使用64位版本的遠端偵錯程式來偵測64位應用程式。 32位和64位進程會使用本機電腦中的區域網路進行通訊。 雖然沒有網路流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> 遠端偵錯程式正在不同的使用者帳戶下執行

根據預設，遠端偵錯程式將只接受來自啟動遠端偵錯程式的使用者和 Administrators 群組成員的連接。 必須明確授與其他使用者的許可權。

您可以使用下列方式的其中之一解決這個問題：

- 在 [遠端偵錯程式] 視窗中，將 Visual Studio 使用者加入遠端偵錯程式的 [許可權] (中，選擇 [ **工具] > 許可權**) 。

- 在遠端電腦上，以您在 Visual Studio 電腦上使用的相同使用者帳戶和密碼，重新開機遠端偵錯程式。

    > [!NOTE]
    > 如果您是在遠端伺服器上執行遠端偵錯程式，請在遠端偵錯程式應用程式上按一下滑鼠右鍵，然後選擇 [ **以系統管理員身分執行** ] (或，您可以) 的服務執行遠端偵錯程式。 如果您不是在遠端伺服器上執行，只要正常啟動即可。

- 您可以從命令列使用 **/allow \<username>** 參數啟動遠端偵錯程式： `msvsmon /allow <username@computer>` 。

- 或者，您可以允許任何使用者進行遠端偵錯。 在遠端偵錯工具視窗中，移至 [工具] > [選項] 對話方塊。 當您選取 [無驗證]   時，可以接著選取 [允許任何使用者執行偵錯] 。 不過，您應該只在其他選項失敗或在私人網路上時，才嘗試此選項。

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> 遠端電腦上的防火牆不允許連入遠端偵錯程式的連接
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>遠端偵錯工具的版本與 Visual Studio 版本不相符
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 若要取得正確的遠端偵錯程式版本，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本機和遠端電腦的驗證模式不同
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 您可以變更驗證模式。 在 [遠端偵錯程式] 視窗中，移至 [ **工具 > 選項** ] 對話方塊。

 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))。

### <a name="anti-virus-software-is-blocking-the-connections"></a>防毒軟體封鎖連線
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊
 檢閱您的網路安全性確定它沒有封鎖通訊。 如需 Windows 網路安全性原則的詳細資訊，請參閱 [安全性原則設定](/windows/device-security/security-policy-settings/security-policy-settings)。

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>網路太忙碌無法支援遠端偵錯
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。

## <a name="more-help"></a>詳細的說明
 若要取得更多的遠端偵錯程式說明，請開啟遠端偵錯程式的說明頁面， (在遠端偵錯程式) 中 **> 使用** 方式。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)
