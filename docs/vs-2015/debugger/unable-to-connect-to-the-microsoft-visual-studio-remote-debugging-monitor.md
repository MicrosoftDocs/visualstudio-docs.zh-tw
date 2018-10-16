---
title: 無法連接到 Microsoft Visual Studio 遠端偵錯監視 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70a186ce1e75f516a08a85e3ce5ec792e6e4a788
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265899"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您在 [附加至處理序]  對話方塊中輸入無效的 Visual Studio 遠端偵錯監視名稱時，就會出現這個錯誤訊息。 遠端偵錯監視的名稱通常與您嘗試為遠端偵錯連接的電腦名稱相同。 這個訊息可能發生的原因，是因為遠端電腦不存在於網路上、遠端電腦上的遠端偵錯監視設定不正確，或是因為網路問題或防火牆的存在，而無法對遠端電腦進行存取。  
  
> [!IMPORTANT]
>  如果您確信收到這則訊息是因為產品錯誤，請向 Visual Studio 報告這個問題： [傳送笑臉](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b)。 如果您需要更多協助，請參閱 [Talk to Us](../ide/talk-to-us.md) 與 Microsoft 連絡。  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>我在本機偵錯時收到這則訊息  
 如果您是在本機偵錯時收到這則訊息，可能要歸責於您的防毒軟體或協力廠商防火牆。 Visual Studio 是 32 位元的應用程式，所以使用 64 位元版本的遠端偵錯工具偵錯 64 位元的應用程式。 這兩種處理序使用本機電腦內的區域網路進行通訊。 雖然沒有網路流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。  
  
 下列章節會列出一些之所以可能收到這則訊息的其他原因，以及修正問題的可行作法。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定已安裝 Visual Studio 遠端偵錯監視，並且正在遠端電腦上執行。 如需遠端偵錯工具和安裝方式的資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
-   在 Visual Studio 中，查看專案屬性 ([專案/屬性/偵錯])。 請確定 [遠端伺服器名稱]  正確。  
  
-   請確認能夠在網路上存取遠端電腦。  
  
## <a name="the-remote-machine-is-not-reachable"></a>找不到遠端電腦  
 請嘗試 [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) 遠端電腦。 如果它不回覆 ping，遠端工具將無法連線。 請嘗試重新啟動遠端電腦，另確定它的網路設定正確。  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>遠端偵錯工具的版本與 Visual Studio 版本不相符  
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 請移至 [下載中心](http://www.microsoft.com/download) ，尋找正確的遠端偵錯工具版本。  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>本機和遠端電腦的驗證模式不同  
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 您可以在 [工具/選項]  對話方塊中變更遠端偵錯工具上的驗證模式。  
  
 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](https://technet.microsoft.com/library/hh831472.aspx)。  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>遠端偵錯工具在不同的使用者帳戶下執行  
 您可以使用下列方式的其中之一解決這個問題：  
  
-   您可以停止遠端偵錯工具，再以使用的本機電腦帳戶重新啟動它。  
  
-   您可以從命令列來啟動遠端偵錯工具 **/allow\<使用者名稱 >** 參數： `msvsmon /allow <username@computer>`  
  
-   您可以將使用者加入遠端偵錯工具的權限 (在遠端偵錯工具視窗：[工具] / [權限] )。  
  
-   如果無法使用前述步驟中的方法，您可以允許任何使用者執行遠端偵錯。 在遠端偵錯工具視窗中，移至 [工具] / [選項]  對話方塊。 當您選取 [無驗證]   時，可以接著選取 [允許任何使用者執行偵錯] 。 不過，您應該只有在沒有任何選擇或在私人網路上，才使用這個選項。  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>遠端電腦上的防火牆不允許連入連線至遠端偵錯工具  
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>防毒軟體封鎖連線  
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊  
 檢閱您的網路安全性確定它沒有封鎖通訊。 如需 Windows 網路安全性原則的詳細資訊，請參閱 [安全性管理](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx)。  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>網路太忙碌無法支援遠端偵錯  
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。  
  
## <a name="more-help"></a>詳細的說明  
 若要取得遠端偵錯工具的詳細說明，包括命令列參數，請在瀏覽器中開啟下列內容：  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>另請參閱  
 [Remote Debugging](../debugger/remote-debugging.md)



