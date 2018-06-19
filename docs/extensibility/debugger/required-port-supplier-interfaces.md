---
title: 所需的連接埠供應商介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e34627effce5e2f0d1401da683536548a32d3f6e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128648"
---
# <a name="required-port-supplier-interfaces"></a>必要的連接埠供應商介面
連接埠提供者必須實作[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面。[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 因為連接埠供應商提供的連接埠時，它也必須實作它們。 因此，它必須實作下列介面：  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     描述該連接埠和可列舉的連接埠上執行的所有處理程序。  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     提供啟動和終止的連接埠上的處理序。  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     提供一種機制，以通知它程式節點建立和解構的這個連接埠的內容中執行的程式。 如需詳細資訊，請參閱[程式節點](../../extensibility/debugger/program-nodes.md)。  
  
-   `IConnectionPointContainer`  
  
     提供的連接點[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)。  
  
## <a name="port-supplier-operation"></a>連接埠供應商作業  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)接收時收到告知處理序和程式建立和終結連接埠上。 連接埠，才能傳送[IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)建立處理程序時， [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)處理程序的連接埠上被終結時。 連接埠也需要將傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)程式建立時和[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)程式的連接埠上執行的處理序中被終結時。  
  
 連接埠通常將程式建立和終結事件以回應[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)和[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法，分別。  
  
 因為連接埠可以啟動和終止處理序實體和邏輯的程式，這些介面也必須由偵錯引擎實作：  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     描述實體的程序。 至少必須實作下列方法：  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     提供方法，讓附加與卸離本身的處理程序 SDM。  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     描述邏輯的程式。 至少必須實作下列方法：  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     提供要附加至這個程式 SDM 的方式。  
  
## <a name="see-also"></a>另請參閱  
 [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)