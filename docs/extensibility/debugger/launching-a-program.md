---
title: 啟動程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 714d751e9855b5567bf76ccd902fada727e14ba1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="launching-a-program"></a>啟動程式
要偵錯程式的使用者可以按 F5 執行偵錯工具從 IDE。 這會開始一系列的事件，最後會導致在 IDE 的連接到偵錯引擎 (DE)，接著連接，或附加，程式，如下所示：  
  
1.  IDE 會先呼叫專案来取得的封裝方案的作用中專案的偵錯設定。 設定包括的起始目錄、 環境變數，在其中執行程式，連接埠，以指定要使用來建立程式，DE。 這些設定會傳遞至偵錯封裝。  
  
2.  如果指定 DE，DE 呼叫作業系統來啟動程式。 由於啟動程式，就會載入程式的執行階段環境。 比方說，如果在 MSIL 中撰寫程式，則 common language runtime 就會被叫用以執行程式。  
  
     -或-  
  
     如果未指定 DE，連接埠就會呼叫作業系統來啟動程式，這會導致要載入的程式的執行階段環境。  
  
    > [!NOTE]
    >  如果將 DE 用於啟動的程式，很可能相同 DE 將會連接到該程式。  
  
3.  根據是否 DE 或連接埠啟動程式，DE 或執行階段環境會建立應用程式的說明或節點，然後通知程式正在執行的連接埠。  
  
    > [!NOTE]
    >  建議執行階段環境中建立程式 節點中，因為程式的節點是可進行偵錯程式的輕量型表示法。 沒有需要載入整個 DE 只是為了建立及註冊程式節點。 如果設計 DE 執行程序在 IDE 中，但沒有可用的 IDE 實際執行中，需要具備的元件，可以將程式節點加入至連接埠。  
  
 新建立的程式，以及任何其他程式相關或不相關、 啟動或附加至相同的 IDE，從撰寫偵錯工作階段。  
  
 以程式設計的方式，當使用者第一次按**F5**，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的偵錯封裝呼叫專案套件 （這是相關聯的啟動程式的型別） 透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法，這個方法會接著填寫<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2>方案的作用中專案的偵錯設定結構。 此結構會傳遞至偵錯封裝呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A>方法。 偵錯封裝接著會執行個體化的工作階段的偵錯管理員 (SDM)，可用來啟動程式正在偵錯，以及任何關聯的偵錯引擎。  
  
 其中一個引數傳遞至 SDM 是用來啟動程式 DE 的 GUID。  
  
 如果不是 DE GUID `GUID_NULL`，SDM DE，會同時建立，然後呼叫其[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法來啟動程式。 例如，如果程式以原生程式碼，然後`IDebugEngineLaunch2::LaunchSuspended`可能會呼叫`CreateProcess`和`ResumeThread`（Win32 函式），以執行程式。  
  
 由於啟動程式，就會載入程式的執行階段環境。 然後建立 DE 或執行階段環境[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)來描述程式介面，並將此介面來傳遞[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)通知程式的連接埠在執行中。  
  
 如果`GUID_NULL`傳遞，則連接埠啟動的程式。 程式開始執行之後，執行階段環境會建立`IDebugProgramNode2`來描述程式介面，並將其傳遞給`IDebugPortNotify2::AddProgramNode`。 這會通知程式正在執行的連接埠。 然後 SDM 附加偵錯引擎執行的程式。  
  
## <a name="in-this-section"></a>本節內容  
 [通知連接埠](../../extensibility/debugger/notifying-the-port.md)  
 說明程式會啟動，而且連接埠會收到通知之後，會發生什麼事。  
  
 [在啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)  
 當偵錯工作階段已準備好將 DE 附加至程式的文件。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。