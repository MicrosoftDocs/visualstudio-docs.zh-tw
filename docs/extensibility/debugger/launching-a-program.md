---
title: 啟動程式 |Microsoft Docs
description: 瞭解當您使用 F5 將程式進行偵錯工具以從 IDE 執行偵錯工具時，所發生的一系列事件。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0dce13e49eeadf4dc02fec07707bebcfe164ed9c
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606693"
---
# <a name="launch-a-program"></a>啟動程式
想要進行程式設計的使用者可以按 **F5** 從 IDE 執行偵錯工具。 這會開始一系列的事件，這些事件最後會導致 IDE 連接到偵錯工具， () 取消連接或附加至程式，如下所示：

1. IDE 會先呼叫專案封裝，以取得方案的作用中專案偵錯工具設定。 這些設定包括起始目錄、環境變數、程式將執行的埠，以及用來建立程式的 [取消] （如果有指定）。 這些設定會傳遞至 debug 套件。

2. 如果指定了 DE，則 DE 會呼叫作業系統來啟動程式。 由於啟動程式的結果，程式的執行時間環境就會載入。 例如，如果程式是以 MSIL 撰寫的，則會叫用 common language runtime 來執行程式。

    -或-

    如果未指定 DE，埠會呼叫作業系統來啟動程式，這會導致程式的執行時間環境載入。

   > [!NOTE]
   > 如果使用 DE 來啟動程式，則可能會將相同的 DE 附加至程式。

3. 根據取消或啟動程式的位置而定，取消的或執行時間環境會建立程式描述或節點，並通知埠程式正在執行。

   > [!NOTE]
   > 建議執行時間環境建立程式節點，因為程式節點是可供偵錯工具的輕量標記法。 不需要載入完整的，只要建立和註冊程式節點即可。 如果回合是設計為在 IDE 的程式中執行，但沒有任何 IDE 實際執行，則需要有可將程式節點新增至埠的元件。

   新建立的程式，以及從相同 IDE 啟動或附加至的任何其他程式（從相同的 IDE 啟動或附加），撰寫一個 debug 會話。

   以程式設計的方式，當使用者第一次按下 **F5** 時， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 debug 封裝會呼叫專案封裝， (與透過方法啟動) 的程式類型相關聯 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> ，然後再以 <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> 方案的使用中專案 debug 設定填滿結構。 此結構會透過呼叫方法傳遞回 debug 封裝 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> 。 然後，debug 封裝會具現化會話 debug manager (SDM) ，它會啟動正在進行調試的程式，以及任何相關聯的偵錯工具引擎。

   傳遞至 SDM 的其中一個引數是用來啟動程式的 DE 的 GUID。

   如果 DE GUID 不是 `GUID_NULL` ，則 SDM 會共同建立 de，然後呼叫其 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 方法來啟動程式。 例如，如果程式是以機器碼撰寫的， `IDebugEngineLaunch2::LaunchSuspended` 則可能會呼叫 `CreateProcess` 並 `ResumeThread` (Win32 函式) 來執行程式。

   啟動程式時，會載入程式的執行時間環境。 取消或執行時間環境會建立 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 介面來描述程式，並將此介面傳遞至 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ，以通知埠程式正在執行。

   如果 `GUID_NULL` 傳遞，則埠會啟動程式。 當程式執行時，執行時間環境會建立 `IDebugProgramNode2` 介面，以描述程式並將它傳遞給 `IDebugPortNotify2::AddProgramNode` 。 這會通知埠程式正在執行。 然後，SDM 會將 debug engine 附加至執行中的程式。

## <a name="in-this-section"></a>本節內容
 [通知埠](../../extensibility/debugger/notifying-the-port.md) 說明在啟動程式之後會發生什麼事，並通知埠。

 在[啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)當偵錯工具準備好將 DE 附加至程式時的檔。

## <a name="related-sections"></a>相關章節
 [調試作業](../../extensibility/debugger/debugging-tasks.md) 包含各種偵錯工具的連結，例如啟動程式和評估運算式。
