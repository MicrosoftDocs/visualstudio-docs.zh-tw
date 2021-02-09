---
title: 工作組遠端登入失敗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f56c8d8e0113b400e9d9cd072ba16f304cd6192
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870840"
---
# <a name="error-workgroup-remote-logon-failure"></a>錯誤：工作群組遠端登入失敗
這個錯誤為：

 登入失敗：不明的使用者名稱或錯誤密碼

 **原因**

 當您從工作群組上的電腦進行偵錯並嘗試連接遠端機器時，就可能會發生這個錯誤。 可能原因包括：

- 遠端機器上沒有符合名稱和密碼的帳戶。

- 如果 Visual Studio 電腦和遠端電腦都位於工作群組中，則發生這個錯誤的原因，可能是因為遠端電腦上的預設 [本機安全性原則] 設定。 [本機安全性原則] 的預設設定是 [僅適用於來賓 - 本機使用者以來賓身分驗證]。 若要在此設定上偵錯，您必須將遠端電腦上的設定變更為 [一般 - 本機使用者以自我身分驗證]。

> [!NOTE]
> 您必須是系統管理員，才能進行下列工作。

### <a name="to-open-the-local-security-policy-window"></a>若要開啟本機安全性原則視窗

1. 啟動 **secpol.msc** Microsoft Management Console 嵌入式管理單元。 在 Windows [搜尋]、Windows [執行] 方塊或在 [命令提示字元] 中輸入 secpol.msc。

### <a name="to-add-user-rights-assignments"></a>若要加入使用者權限指派

1. 開啟 [本機安全性原則] 視窗。

2. 展開 [本機原則] 資料夾。

3. 按一下 **[使用者權限指派]**。

4. 在 [原則] 一欄中，按兩下 [偵錯程式] 來檢視 [本機安全性原則設定] 對話方塊中的目前本機群組原則指派。

     ![本機安全性原則使用者權限](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. 若要新增使用者，請按一下 [新增使用者或群組] 按鈕。

### <a name="to-change-the-sharing-and-security-model"></a>若要變更共用和安全性模式

1. 開啟 [本機安全性原則] 視窗。

2. 展開 [本機原則] 資料夾。

3. 按一下 [安全性選項]。

4. 在 [原則] 欄中按兩下 [網路存取: 本機帳戶的共用和資訊安全模型]。

5. 在 [網路存取: 本機帳戶的共用和資訊安全模型] 對話方塊中，將值變更為 [傳統 - 本機使用者自我驗證]，然後按一下 [套用] 按鈕。

     ![本機安全性原則安全性選項](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [遠端偵錯](../debugger/remote-debugging.md)