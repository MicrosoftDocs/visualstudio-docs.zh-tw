---
title: 無法進行調試 &apos; 程式，因為系統上已啟用內核偵錯工具 |Microsoft 檔
description: 當您嘗試在 Windows 7 或 Windows Vista 系統上（已在「偵測模式」中啟動）偵測 managed 程式碼，且應用程式使用 CLR 版本 CLR 2.0、3.0 或3.5 時，就會出現此訊息。
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ced7fb79a11321678ae2963241807e5ddd4600ab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466455"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>錯誤：因為系統上已啟用內核偵錯工具，所以無法進行&#39;t 的偵錯工具
當您對 Managed 程式碼進行偵錯時，可能會收到下列錯誤訊息：

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 當您嘗試對 Managed 程式碼進行偵錯時，這個訊息就會出現：

- 在 [!INCLUDE[win7](../debugger/includes/win7_md.md)] 或 [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] 系統上，以偵測模式啟動。

- 使用 CLR 2.0、3.0 或 3.5 版的應用程式。

## <a name="solution"></a>解決方案

#### <a name="to-fix-this-problem"></a>若要修復這個問題

- 將您的應用程式升級為使用 CLR 4.0 或 4.5 版

   – 或 –

- 停用核心偵錯而以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 進行偵錯。

   – 或 –

- 使用核心偵錯工具進行偵錯，不要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

   – 或 –

- 在核心偵錯工具中，停用使用者模式例外狀況。

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>若要在目前工作階段中停用核心偵錯

- 在命令提示字元中，輸入：

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>若要停用所有工作階段的核心偵錯 (Windows Vista 和 Windows 7)

1. 在命令提示字元中，輸入：

    ```cmd
    bcdedit /debug off
    ```

2. 重新啟動電腦。

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>若要停用所有工作階段的核心偵錯 (其他 Windows 作業系統)

1. 在您的系統磁碟機 (通常是 C:\\) 上尋找 boot.ini。 boot.ini 檔案可能為隱藏或唯讀狀態。 因此，您必須使用下列命令才能看見該檔案：

    ```cmd
    dir /ASH
    ```

2. 使用 [記事本] 開啟 boot.ini 並移除下列選項：

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. 重新啟動電腦。

#### <a name="to-debug-with-the-kernel-debugger"></a>若要使用核心偵錯工具進行偵錯

1. 如果已經連結核心偵錯工具，您將看到一則訊息，詢問您是否要繼續進行偵錯。 按一下這個按鈕繼續進行。

2. 您也可能會收到 `User break exception(Int 3).`。如果發生這種情況，請輸入下列核心偵錯工具命令繼續進行偵錯：

     `gn`

## <a name="see-also"></a>另請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
