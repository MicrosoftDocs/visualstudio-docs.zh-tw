---
title: 錯誤： 偵錯目前&#39;t 可能因為在系統上已啟用核心偵錯 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba943057da003a0fafee6d6fb8c6082d228779f9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>錯誤： 偵錯目前&#39;t 可能因為在系統上已啟用核心偵錯工具
當您對 Managed 程式碼進行偵錯時，可能會收到下列錯誤訊息：  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 當您嘗試對 Managed 程式碼進行偵錯時，這個訊息就會出現：  
  
-   在以偵錯模式啟動的 [!INCLUDE[win7](../debugger/includes/win7_md.md)] 或 [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] 系統上。  
  
-   使用 CLR 2.0、3.0 或 3.5 版的應用程式。  
  
## <a name="solution"></a>方案  
  
#### <a name="to-fix-this-problem"></a>若要修復這個問題  
  
-   將您的應用程式升級為使用 CLR 4.0 或 4.5 版  
  
     -或-  
  
-   停用核心偵錯而以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 進行偵錯。  
  
     -或-  
  
-   使用核心偵錯工具進行偵錯，不要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     -或-  
  
-   在核心偵錯工具中，停用使用者模式例外狀況。  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>若要在目前工作階段中停用核心偵錯  
  
-   在命令提示中，輸入：  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>若要停用所有工作階段的核心偵錯 (Windows Vista 和 Windows 7)  
  
1.  在命令提示中，輸入：  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  重新啟動電腦。  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>若要停用所有工作階段的核心偵錯 (其他 Windows 作業系統)  
  
1.  在您的系統磁碟機上尋找 boot.ini (通常是 c:\\)。 boot.ini 檔案可能為隱藏或唯讀狀態。 因此，您必須使用下列命令才能看見該檔案：  
  
    ```  
    dir /ASH  
    ```  
  
2.  使用 [記事本] 開啟 boot.ini 並移除下列選項：  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  重新啟動電腦。  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>若要使用核心偵錯工具進行偵錯  
  
1.  如果已經連結核心偵錯工具，您將看到一則訊息，詢問您是否要繼續進行偵錯。 按一下這個按鈕繼續進行。  
  
2.  您也可能會收到 `User break exception(Int 3).`。如果發生這種情況，請輸入下列核心偵錯工具命令繼續進行偵錯：  
  
     `gn`  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)