---
title: "無法連線到 Microsoft Visual Studio 遠端偵錯監視 |Microsoft 文件"
ms.custom: 
ms.date: 08/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3484ac7aa26f630245a471a234dd19468e50ebf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
此訊息可能是因為遠端偵錯監視已不正確設定遠端電腦上或遠端電腦因為網路問題或防火牆的存在而無法存取。
  
> [!IMPORTANT]
>  如果您認為您收到這個訊息是因為產品錯誤，請[報告這個問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)Visual studio。 如果您需要更多協助，請參閱 [Talk to Us](../ide/talk-to-us.md) 與 Microsoft 連絡。

## <a name="specificerrors"></a>什麼是詳細的錯誤訊息？

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor`訊息是泛型。 通常，更特定的訊息包含在錯誤的字串，而且可以協助您找出問題或搜尋更精確的修正程式的原因。 以下是一些較常見的錯誤訊息，附加到主要的錯誤訊息：

- [偵錯工具無法連線到遠端電腦。偵錯工具無法解析指定的電腦名稱](#cannot_connect)
- [連接要求遭到遠端偵錯工具拒絕](#rejected)
- [存取記憶體位置無效](#invalid_access)
- [沒有伺服器，以在遠端電腦上執行指定的名稱](#no_server)
- [要求的名稱有效，但找不到要求類型的資料](#valid_name)
- [Visual Studio 遠端偵錯工具在目標電腦上無法連回這部電腦](#cant_connect_back)
- [拒絕存取](#access_denied)
- [發生安全性封裝特定錯誤](#security_package)

## <a name="cannot_connect"></a>偵錯工具無法連線到遠端電腦。 偵錯工具無法解析指定的電腦名稱

請嘗試下列步驟：

1. 請確定您輸入有效的電腦名稱和連接埠號碼在**附加至處理序**對話方塊中或在專案屬性中 (若要設定屬性，請參閱[步驟](#server_incorrect))。 電腦名稱必須是下列格式：

    `computername:port`

    > [!NOTE]
    > 連接埠號碼必須符合[遠端偵錯工具的連接埠編號](../debugger/remote-debugger-port-assignments.md)、 哪些*必須執行*目標電腦上。

2. 如果電腦名稱無法運作，請嘗試 IP 位址，並改為連接埠號碼。

3. 請確定目標電腦上執行遠端偵錯工具的版本符合您的 Visual Studio 版本。 若要取得正確的遠端偵錯工具版本，請參閱[遠端偵錯](../debugger/remote-debugging.md)。

    > [!TIP]
    > 如果您要將附加至處理程序，而且您連線成功，但看不到您想要的程序，選取**顯示所有使用者 核取方塊的處理序**。 這會顯示處理程序是否您連接不同的使用者帳戶。

4. 如果這些步驟無法解決此錯誤，請參閱[找不到遠端電腦](#dns)。

## <a name="rejected"></a>連接要求遭到遠端偵錯工具拒絕

在**附加至處理序**對話方塊方塊中，或在專案屬性，請確定遠端電腦名稱和連接埠號碼符合遠端偵錯工具視窗中顯示的名稱和連接埠號碼。 如果不正確，請修正，然後再試一次。

如果這些值是否正確，訊息會提及**Windows 驗證**模式中，檢查遠端偵錯工具是否在正確的驗證模式 (**工具 > 選項**)。

## <a name="invalid_access"></a>存取記憶體位置無效

發生內部錯誤。 重新啟動 Visual Studio 並再試一次。

## <a name="no_server"></a>沒有伺服器，以在遠端電腦上執行指定的名稱

Visual Studio 無法連接到遠端偵錯工具。 此訊息可能會發生數個原因：

- 遠端偵錯工具可能在不同的使用者帳戶下執行。 請參閱[這些步驟](#user_accounts)

- 防火牆會封鎖連接埠。 請確定防火牆為[不會封鎖您的要求](#firewall)，特別是當您使用協力廠商防火牆。

- 遠端偵錯工具版本不符合 Visual Studio。 若要取得正確的遠端偵錯工具版本，請參閱[遠端偵錯](../debugger/remote-debugging.md)


## <a name="#valid_name"></a>要求的名稱有效，但找不到要求類型的資料

遠端電腦已經存在，但 Visual Studio 無法連接到遠端偵錯工具。 此訊息可能會發生數個原因：

- DNS 問題禁止該連線。 請參閱[步驟](#dns)。

- 遠端偵錯工具可能在不同的使用者帳戶下執行。 請遵循[步驟](#user_accounts)。

- 防火牆會封鎖連接埠。 請確定防火牆為[不會封鎖您的要求](#firewall)，特別是當您使用協力廠商防火牆。

- 遠端偵錯工具版本不符合 Visual Studio。 若要取得正確的遠端偵錯工具版本，請參閱[遠端偵錯](../debugger/remote-debugging.md)。

## <a name="cant_connect_back"></a>Visual Studio 遠端偵錯工具在目標電腦上無法連回這部電腦

遠端偵錯工具可能在不同的使用者帳戶下執行。 在 遠端偵錯工具中，開啟**工具 > 權限**將使用者新增至遠端偵錯工具的權限。 如需詳細資訊，請參閱[不同的使用者帳戶下執行遠端偵錯工具](#user_accounts)。

如果錯誤訊息也會提及防火牆，在本機電腦上的防火牆可能會導致回到 Visual Studio 從遠端電腦通訊。 請參閱[步驟](#firewall)。

## <a name="access_denied"></a>拒絕存取

如果您嘗試偵錯 64 位元遠端電腦 （不支援） 的 32 位元電腦上，可能會看到這個錯誤。

## <a name="security_package"></a>發生安全性封裝特定錯誤

這可能是舊版的 Windows XP 和 Windows 7 的特定問題。 請參閱此[資訊](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)。 

## <a name="causes-and-recommendations"></a>原因和建議

### <a name="dns"></a>找不到遠端電腦 

如果您無法連接使用的遠端電腦名稱，請嘗試改為使用 IP 位址。 您可以使用`ipconfig`取得 IPv4 位址在遠端電腦上的命令列。 如果您使用的主機檔案，請確認已正確設定。

如果失敗，請確定遠端電腦可存取網路上 ([ping](https://technet.microsoft.com/en-us/library/cc732509(v=ws.10).aspx)遠端電腦)。 不支援透過網際網路的遠端偵錯，除非在某些案例中 Microsoft Azure。
  
### <a name="server_incorrect"></a>伺服器名稱不正確，或協力廠商軟體干擾遠端偵錯工具

在 Visual Studio 中，查看專案屬性，請確定伺服器名稱正確。 請參閱主題[C# 和 Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp)和[c + +](../debugger/remote-debugging-cpp.md#remote_cplusplus)。 Asp.net、 開啟**屬性 / Web / 伺服器**或**屬性 / 偵錯**視專案類型而定。

> [!NOTE]
> 如果您要將附加至處理程序，將不會使用專案屬性中的遠端設定。

伺服器名稱正確無誤，如果您的防毒軟體或協力廠商防火牆可能封鎖了遠端偵錯工具。 當在本機偵錯，這可能是因為 Visual Studio 是 32 位元應用程式，因此它會使用 64 位元版本的遠端偵錯工具偵錯 64 位元應用程式。 使用本機電腦內的區域網路進行通訊的 32 位元和 64 位元處理程序。 雖然沒有網路流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。

### <a name="user_accounts"></a>在不同的使用者帳戶下執行遠端偵錯工具 

遠端偵錯工具，根據預設，只接受來自啟動遠端偵錯工具和系統管理員群組的成員之使用者的連線。 其他使用者必須明確授與權限。 
 
您可以使用下列方式的其中之一解決這個問題：  

-   Visual Studio 使用者加入遠端偵錯工具的權限 (在遠端偵錯工具視窗中，選擇 **工具 > 權限**)。

-   遠端電腦上，重新啟動遠端偵錯工具在相同的使用者帳戶及您使用 Visual Studio 電腦的密碼。

    > [!NOTE]
    > 如果您在遠端伺服器上執行遠端偵錯工具，以滑鼠右鍵按一下 遠端偵錯工具應用程式，並選擇**系統管理員身分執行**（或您可以執行遠端偵錯工具當做服務）。 如果您不遠端伺服器上執行它，只要正常方式啟動。
  
-   您可以從命令列啟動遠端偵錯工具**/ 允許\<使用者名稱 >**參數： `msvsmon /allow <username@computer>`。 
  
-   或者，您可以允許任何使用者執行遠端偵錯。 在遠端偵錯工具視窗中，移至**工具 > 選項**對話方塊。 當您選取 [無驗證]   時，可以接著選取 [允許任何使用者執行偵錯] 。 不過，您應該嘗試此選項，只有當其他選項失敗，或如果您是在私人網路上。

### <a name="firewall"></a>遠端電腦上的防火牆不允許遠端偵錯工具的連入連線  
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>遠端偵錯工具的版本不符 Visual Studio 的版本  
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 若要取得正確的遠端偵錯工具版本，請參閱[遠端偵錯](../debugger/remote-debugging.md)。
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本機和遠端電腦的驗證模式不同  
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 您可以變更驗證模式。 在遠端偵錯工具視窗中，移至**工具 > 選項** 對話方塊。
  
 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](https://technet.microsoft.com/en-us/library/hh831472.aspx)。   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>防毒軟體封鎖連線  
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊  
 檢閱您的網路安全性確定它沒有封鎖通訊。 如需 Windows 網路安全性原則的詳細資訊，請參閱[安全性原則設定](/windows/device-security/security-policy-settings/security-policy-settings)。  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>網路太忙碌無法支援遠端偵錯  
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。  
  
## <a name="more-help"></a>詳細的說明  
 若要取得更多的遠端偵錯工具的說明，請開啟 遠端偵錯工具的 說明 頁面 (**協助 > 使用量**遠端偵錯工具中)。
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯](../debugger/remote-debugging.md)