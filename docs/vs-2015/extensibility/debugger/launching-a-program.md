---
title: 啟動程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27b7daadd3642a4eb35d993e37b6ade3bd829972
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242542"
---
# <a name="launching-a-program"></a>啟動程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

想要偵錯程式的使用者可以按 F5 以執行從 IDE 的偵錯工具。 這樣就會開始一系列的最終會導致 IDE 連接到偵錯引擎 (DE)，依序連接，或附加，給程式，如下所示的事件：  
  
1.  IDE 會先呼叫以取得解決方案的使用中專案的偵錯設定專案套件。 設定包括的起始目錄、 環境變數，在其中執行程式，連接埠，以指定要使用來建立程式，DE。 這些設定會傳遞至偵錯封裝。  
  
2.  如果指定規定，DE 呼叫啟動程式的作業系統。 由於啟動程式，會載入程式的執行階段環境。 比方說，如果在 MSIL 中撰寫程式，則 common language runtime 就會被叫用以執行程式。  
  
     -或-  
  
     如果未指定規定，連接埠就會呼叫啟動程式，這會導致要載入程式的執行階段環境的作業系統。  
  
    > [!NOTE]
    >  如果使用規定來啟動程式，很可能相同 DE，會附加至程式。  
  
3.  根據是否 DE 或連接埠啟動程式，DE 或執行階段環境建立計劃的描述或節點，然後通知程式正在執行中的連接埠。  
  
    > [!NOTE]
    >  建議的執行階段環境，建立程式 節點中，因為程式的節點是可偵錯之程式的輕量型表示法。 就不需要載入整個 DE 就來建立及註冊程式 節點。 如果是 DE 執行 IDE，但沒有 IDE 的過程中實際執行，需要有一個元件，可以將程式節點加入至連接埠。  
  
 新建立的程式，以及任何其他程式相關或不相關、 啟動或附加至相同的 IDE 中，從撰寫偵錯工作階段。  
  
 以程式設計的方式，當使用者第一次按下**F5**，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]的套件偵錯呼叫專案套件 （也就是相關聯程式正在啟動的型別） 透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法，這個方法會接著填寫<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>解決方案的使用中專案的偵錯設定結構。 此結構，會透過呼叫傳遞回到偵錯封裝<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>方法。 偵錯封裝接著會執行個體化工作階段的偵錯管理員 (SDM)，可用來啟動程式正在偵錯，以及任何關聯的偵錯引擎。  
  
 其中一個引數傳遞至 SDM 是用來啟動程式 DE 的 GUID。  
  
 如果不是 DE GUID `GUID_NULL`，SDM DE，會同時建立，然後呼叫其[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法來啟動程式。 例如，如果程式以原生程式碼，然後`IDebugEngineLaunch2::LaunchSuspended`可能會呼叫`CreateProcess`和`ResumeThread`（Win32 函式），以執行程式。  
  
 由於啟動程式，會載入程式的執行階段環境。 DE 或執行階段環境然後建立[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)介面來描述程式，並傳遞此介面，以便[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)通知程式的連接埠在執行中。  
  
 如果`GUID_NULL`傳遞，則連接埠啟動的程式。 當程式執行時，執行階段環境會建立`IDebugProgramNode2`介面來描述程式，並將它傳遞給`IDebugPortNotify2::AddProgramNode`。 這會通知程式正在執行中的連接埠。 然後在 SDM 會將偵錯引擎附加至執行中的程式。  
  
## <a name="in-this-section"></a>本節內容  
 [通知連接埠](../../extensibility/debugger/notifying-the-port.md)  
 說明程式會啟動，而且該連接埠會收到通知之後，會發生什麼事。  
  
 [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)  
 當偵錯工作階段已準備好將 DE 附加至程式的文件。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。

