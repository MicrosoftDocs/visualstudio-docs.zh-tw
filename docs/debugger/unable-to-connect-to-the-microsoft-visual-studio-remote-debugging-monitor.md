---
title: 無法連接至 Microsoft Visual Studio 遠端偵錯監視 |Microsoft Docs
ms.date: 08/24/2017
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
ms.openlocfilehash: a2a3f4429341ecdba26dab2f95415332f9cb2eca
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187261"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
可能會發生此訊息，是因為遠端電腦上的遠端偵錯「監視」設定不正確，或遠端電腦因為網路問題或防火牆出現而無法存取。

> [!IMPORTANT]
> 如果您認為您因為產品錯誤而收到此訊息，請將[此問題](../ide/how-to-report-a-problem-with-visual-studio.md)回報給 Visual Studio。 如果您需要更多協助，請參閱 [Talk to Us](../ide/feedback-options.md) 與 Microsoft 連絡。

## <a name="specificerrors"></a>詳細的錯誤訊息是什麼？

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` 訊息為泛型。 通常，錯誤字串中會包含更特定的訊息，並可協助您找出問題的原因，或搜尋更精確的修正程式。 以下是附加至主要錯誤訊息的一些較常見的錯誤訊息：

- [偵錯工具無法連接到遠端電腦。偵錯工具無法解析指定的電腦名稱稱](#cannot_connect)
- [遠端偵錯程式拒絕連接要求](#rejected)
- [對記憶體位置的存取無效](#invalid_access)
- [在遠端電腦上執行的指定名稱沒有伺服器](#no_server)
- [要求的名稱有效，但找不到要求類型的資料](#valid_name)
- [目的電腦上的 Visual Studio 遠端偵錯工具無法連回這部電腦](#cant_connect_back)
- [拒絕存取](#access_denied)
- [發生安全性封裝特定的錯誤](#security_package)

## <a name="cannot_connect"></a>偵錯工具無法連接到遠端電腦。 偵錯工具無法解析指定的電腦名稱稱

請嘗試下列步驟：

1. 請確定您在 [**附加至進程**] 對話方塊或專案屬性中輸入有效的電腦名稱稱和埠號碼（若要設定屬性，請參閱[下列步驟](#server_incorrect)）。 電腦名稱稱必須是下列格式：

    `computername:port`

    > [!NOTE]
    > 埠號碼必須符合*必須*在目的電腦上執行之[遠端偵錯程式的埠號碼](../debugger/remote-debugger-port-assignments.md)。

2. 如果電腦名稱稱無法運作，請改為嘗試 IP 位址和埠號碼。

3. 請確定目的電腦上執行的遠端偵錯程式版本符合您的 Visual Studio 版本。 若要取得正確版本的遠端偵錯程式，請參閱[遠端](../debugger/remote-debugging.md)偵測。

    > [!TIP]
    > 如果您要附加至進程並成功連線，但沒有看到您想要的進程，請選取 [**顯示所有使用者的進程] 核取方塊**。 如果您是以不同的使用者帳戶連線，這會顯示進程。

4. 如果這些步驟無法解決此錯誤，請參閱[無法連線到遠端電腦](#dns)。

## <a name="rejected"></a>遠端偵錯程式拒絕連接要求

在 [**附加至進程**] 對話方塊或 [專案屬性] 中，確定遠端電腦名稱稱和埠號碼符合 [遠端偵錯程式] 視窗中顯示的名稱和埠號碼。 如果不正確，請修正並再試一次。

如果這些值是正確的，而且訊息提及**Windows 驗證**模式，請檢查遠端偵錯程式是否處於正確的驗證模式（[**工具] > 選項**）。

## <a name="invalid_access"></a>對記憶體位置的存取無效

發生內部錯誤。 請重新開機 Visual Studio，然後再試一次。

## <a name="no_server"></a>在遠端電腦上執行的指定名稱沒有伺服器

Visual Studio 無法連接到遠端偵錯程式。 此訊息可能會發生的原因有好幾個：

- 遠端偵錯程式可能會在不同的使用者帳戶下執行。 請參閱[下列步驟](#user_accounts)

- 防火牆上的埠遭到封鎖。 請確定防火牆不會[封鎖您的要求](#firewall)，特別是在您使用協力廠商防火牆的情況下。

- 遠端偵錯程式版本不符合 Visual Studio。 若要取得正確版本的遠端偵錯程式，請參閱[遠端](../debugger/remote-debugging.md)偵測。

## <a name="valid_name"></a>要求的名稱有效，但找不到要求類型的資料

遠端電腦存在，但 Visual Studio 無法連接到遠端偵錯程式。 此訊息可能會發生的原因有好幾個：

- DNS 問題導致連線無法執行。 請參閱[下列步驟](#dns)。

- 遠端偵錯程式可能會在不同的使用者帳戶下執行。 請遵循[以下步驟](#user_accounts)。

- 防火牆上的埠遭到封鎖。 請確定防火牆不會[封鎖您的要求](#firewall)，特別是在您使用協力廠商防火牆的情況下。

- 遠端偵錯程式版本不符合 Visual Studio。 若要取得正確版本的遠端偵錯程式，請參閱[遠端](../debugger/remote-debugging.md)偵測。

## <a name="cant_connect_back"></a>目的電腦上的 Visual Studio 遠端偵錯工具無法連回這部電腦

遠端偵錯程式可能會在不同的使用者帳戶下執行。 在遠端偵錯程式中，開啟 [**工具] > [許可權**]，將使用者加入遠端偵錯程式的許可權。 如需詳細資訊，請參閱[遠端偵錯程式在不同的使用者帳戶下](#user_accounts)執行。

如果錯誤訊息也提及防火牆，本機電腦上的防火牆可能會阻止遠端電腦的通訊回到 Visual Studio。 請參閱[下列步驟](#firewall)。

## <a name="access_denied"></a> 拒絕存取

如果您嘗試從32位的電腦（不支援）在64位的遠端電腦上進行調試，就可能會看到此錯誤。

## <a name="security_package"></a>發生安全性封裝特定的錯誤

這可能是 Windows XP 和 Windows 7 特有的舊版問題。 請參閱這則[資訊](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)。

## <a name="causes-and-recommendations"></a>原因和建議

### <a name="dns"></a> 找不到遠端電腦

如果您無法使用遠端電腦名稱稱進行連接，請嘗試改用 IP 位址。 您可以在遠端電腦上的命令列中使用 `ipconfig`，以取得 IPv4 位址。 如果您使用 HOSTS 檔案，請確認它已正確設定。

如果失敗，請確認遠端電腦是否可在網路上存取（[ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10))遠端電腦）。 除非在某些 Microsoft Azure 案例中，否則不支援透過網際網路進行遠端偵測。

### <a name="server_incorrect"></a>伺服器名稱不正確，或協力廠商軟體與遠端偵錯程式干擾

在 Visual Studio 中，查看專案屬性，並確認伺服器名稱正確。 請參閱的[ C#主題，並 Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp)和[C++](../debugger/remote-debugging-cpp.md#remote_cplusplus)。 針對 ASP.NET，請根據您的專案類型開啟 [**屬性]/[Web/伺服器**] 或 [**屬性]/[Debug** ]。

> [!NOTE]
> 如果您要附加至進程，則不會使用專案屬性中的遠端設定。

如果伺服器名稱正確，防毒軟體或協力廠商防火牆可能會封鎖遠端偵錯程式。 在本機進行偵錯工具時，可能會發生這種情況，因為 Visual Studio 是32位的應用程式，所以它會使用64位版本的遠端偵錯程式來偵測64位應用程式。 32位和64位進程會使用本機電腦內的區域網路進行通訊。 雖然沒有網路流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。

### <a name="user_accounts"></a> 遠端偵錯工具在不同的使用者帳戶下執行

遠端偵錯程式預設只接受啟動遠端偵錯程式的使用者與 Administrators 群組成員的連接。 必須明確授與其他使用者的許可權。

您可以使用下列方式的其中之一解決這個問題：

- 將 Visual Studio 使用者加入遠端偵錯程式的許可權（在遠端偵錯程式視窗中，選擇 [工具] [>] [**許可權**]）。

- 在遠端電腦上，以您在 Visual Studio 電腦上使用的相同使用者帳戶和密碼重新開機遠端偵錯程式。

    > [!NOTE]
    > 如果您在遠端伺服器上執行遠端偵錯程式，請以滑鼠右鍵按一下 [遠端偵錯程式] 應用程式，然後選擇 [以**系統管理員身分執行**] （或者，您可以將遠端偵錯程式當做服務執行）。 如果您不是在遠端伺服器上執行，只要正常啟動就可以了。

- 您可以從命令列使用 **/allow \<使用者名稱>** 參數：`msvsmon /allow <username@computer>` 啟動遠端偵錯工具。

- 或者，您可以允許任何使用者執行遠端偵錯。 在遠端偵錯工具視窗中，移至 [工具] > [選項] 對話方塊。 當您選取 [無驗證]時，可以接著選取 [允許任何使用者執行偵錯]。 不過，只有當其他選項失敗時，或如果您是在私人網路上，您才應該嘗試此選項。

### <a name="firewall"></a> 遠端電腦上的防火牆不允許連入連線至遠端偵錯工具
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>遠端偵錯工具的版本與 Visual Studio 版本不相符
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 若要取得正確版本的遠端偵錯程式，請參閱[遠端](../debugger/remote-debugging.md)偵測。

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本機和遠端電腦的驗證模式不同
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 您可以變更驗證模式。 在 [遠端偵錯程式] 視窗中，移至 [工具] [ **> 選項**] 對話方塊。

 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))。

### <a name="anti-virus-software-is-blocking-the-connections"></a>防毒軟體封鎖連線
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊
 檢閱您的網路安全性確定它沒有封鎖通訊。 如需 Windows 網路安全性原則的詳細資訊，請參閱[安全性原則設定](/windows/device-security/security-policy-settings/security-policy-settings)。

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>網路太忙碌無法支援遠端偵錯
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。

## <a name="more-help"></a>詳細的說明
 若要取得更多遠端偵錯程式說明，請開啟遠端偵錯程式的 [說明] 頁面（說明如何在遠端偵錯程式中 **> 使用**方式）。

## <a name="see-also"></a>請參閱
- [Remote Debugging](../debugger/remote-debugging.md)
