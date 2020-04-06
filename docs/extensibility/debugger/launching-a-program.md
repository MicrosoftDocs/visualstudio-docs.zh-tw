---
title: 啟動計劃 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738472"
---
# <a name="launch-a-program"></a>啟動程式
想要調試程式的用戶可以按**F5**從 IDE 運行除錯器。 這將啟動一系列事件,最終導致 IDE 連接到除錯引擎 (DE),調試引擎又連接到程式,如下所示:

1. IDE 首先調用專案包以獲取解決方案的活動專案調試設置。 這些設置包括起始目錄、環境變數、程式將在其中運行的埠以及用於創建程式的 DE(如果指定)。 這些設置將傳遞到調試包。

2. 如果指定了 DE,DE 將調用作業系統來啟動程式。 啟動程式後,程式的運行時環境將載入。 例如,如果程式是在 MSIL 中編寫的,則將調用通用語言運行時來運行該程式。

    -或-

    如果未指定 DE,埠將調用作業系統啟動程式,這將導致載入程式的執行時環境。

   > [!NOTE]
   > 如果 DE 用於啟動程式,則同一 DE 很可能將附加到該程式。

3. 根據 DE 還是連接埠啟動程式,DE 或執行時環境然後創建程式說明或節點,並通知埠程式正在執行。

   > [!NOTE]
   > 建議運行時環境創建程式節點,因為程式節點是可調試的程序的羽量級表示形式。 無需僅載入整個 DE 來創建和註冊程式節點。 如果 DE 設計為在 IDE 過程中運行,但實際沒有 IDE 運行,則需要有一個元件可以將程式節點添加到埠。

   新創建的程式以及從同一 IDE 啟動或附加到的任何其他程式(相關或不相關程式)組成調試會話。

   在程式設計上,當使用者首次按**F5**時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],除錯<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>套件透過方法調用專案套件(與正在啟動的程式類型相關聯),該方法又使用解決方案的活動專案調試設置<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>填充 結構。 此結構通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>方法傳回調試包。 然後,調試包實例化會話調試管理器 (SDM),該管理器啟動正在調試的程式和任何關聯的調試引擎。

   傳遞給 SDM 的參數之一是用於啟動程式的 DE 的 GUID。

   如果 DE`GUID_NULL`GUID 不是 ,則 SDM 共同建立 DE,然後調用其[Launch 暫停](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法啟動程式。 例如,如果程式是用本機代碼編寫的,`IDebugEngineLaunch2::LaunchSuspended`則可能會調`CreateProcess`用`ResumeThread`和 (Win32 函數)來運行該程式。

   啟動程式後,將載入程式的運行時環境。 然後,DE 或運行時環境創建一個[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面來描述程式,並將此介面傳遞給[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)以通知埠程式正在運行。

   如果`GUID_NULL`傳遞,則埠將啟動該程式。 執行程式執行後,執行時環境會建立一`IDebugProgramNode2`個介面來描述程式並將其傳遞`IDebugPortNotify2::AddProgramNode`給 。 這將通知埠程式正在運行。 然後 SDM 將調試引擎附加到正在運行的程式。

## <a name="in-this-section"></a>本節內容
 [通知連接埠](../../extensibility/debugger/notifying-the-port.md)說明程序啟動後會發生什麼情況,並通知埠。

 [啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)當調試會話準備好將 DE 附加到程式時,將記錄。

## <a name="related-sections"></a>相關章節
 [除錯工作](../../extensibility/debugger/debugging-tasks.md)包含指向各種除錯任務的連結,例如啟動程式和評估運算式。
