---
title: 無法附加至進程 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
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
ms.openlocfilehash: 22d798d30d09cb509f53d093ae61bb1a02b414ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728881"
---
# <a name="unable-to-attach-to-the-process"></a>無法附加到處理序
無法附加至處理序。 當連接至這部電腦時，伺服器上的偵錯工具元件會收到拒絕存取。

 有兩種常見的案例是造成此錯誤的原因：

 案例電腦 A 正在執行 Windows XP。 電腦 B 執行的是 Windows Server 2003。 電腦 B 上的登錄會包含下列 DWORD 值：

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 使用者 1 在電腦 B 上啟動終端伺服器工作階段 (工作階段 1)，並從該工作階段啟動 Managed 應用程式。

 使用者2（這兩部電腦上的系統管理員）都會登入電腦 A。他或她嘗試附加到電腦 B 上的會話1中執行的應用程式。

 案例一個使用者登入了兩部機器，A 和 B，在相同群組中，兩台電腦上使用相同的密碼。 偵錯工具正在電腦 A 上執行，並嘗試附加至在電腦 B 上執行的受控應用程式。電腦 A 具有**網路存取：本機帳戶的共用和安全性模式**設定為 [**來賓**]。

### <a name="to-solve-scenario-1"></a>解決案例 1

- 以相同使用者帳戶名稱和密碼，執行偵錯工具和 Managed 應用程式。

### <a name="to-solve-scenario-2"></a>解決案例 2

1. 在 [開始] 功能表內選擇 [控制台]。

2. 在 [控制台] 中按兩下 [系統管理工具]。

3. 在 [系統管理工具] 視窗中按兩下 [本機安全性原則]。

4. 在 [本機安全性原則] 視窗中選取 [本機原則]。

5. 在 [原則] 欄中按兩下 [網路存取: 本機帳戶的共用和資訊安全模型]。

6. 在 [網路存取: 本機帳戶的共用和資訊安全模型] 對話方塊中，將本機安全性設定變更為 [傳統]，再按一下 [確定]。

    > [!CAUTION]
    > 將安全性模式變更為 [一般]，會導致未預期存取共用檔案和 DCOM 元件。 如果您做了此變更，遠端使用者可以使用您的本機使用者帳戶驗證，而非使用來賓帳戶。 如果遠端使用者符合您的使用者名稱和密碼，該使用者將可以存取您已共用的任何資料夾或 DCOM 物件。如果您使用此安全性模型，請確定電腦上的所有使用者帳戶都具有強式密碼，或為偵錯工具和所調試的電腦設定隔離的網路島，以防止未經授權的存取。

7. 關閉所有視窗。

## <a name="see-also"></a>請參閱
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)