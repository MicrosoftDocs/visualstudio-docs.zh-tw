---
title: 所需的連接埠供應商介面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcb8bae5d715e59591eb44418de2b36e8ac753a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112503"
---
# <a name="required-port-supplier-interfaces"></a>必要的連接埠供應商介面
連接埠提供者必須實作[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面。[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 連接埠提供者提供的連接埠，並且加以實作。 因此，它必須執行下列介面：

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

     描述該連接埠，並列舉所有的連接埠上執行的處理程序。

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

     提供啟動和終止的連接埠上的處理序。

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

     提供一個機制，以通知它程式節點的建立和解構的這個連接埠的內容中執行的程式。 如需詳細資訊，請參閱 <<c0> [ 程式節點](../../extensibility/debugger/program-nodes.md)。

- `IConnectionPointContainer`

     提供的連接點[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)。

## <a name="port-supplier-operation"></a>連接埠供應商的作業
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)接收會收到通知時處理序，然後建立並終結的連接埠上的程式。 連接埠，才能傳送[IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)處理程序建立時並[IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)處理程序時終結的連接埠。 連接埠也需要傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)程式建立時並[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)程式中的連接埠上執行的程序時損毀。

 連接埠通常會傳送程式建立和終結事件以回應[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)並[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法，分別。

 因為連接埠可以啟動和終止處理序實體和邏輯的程式，偵錯引擎也必須實作下列介面：

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

     描述實體的程序。 至少必須實作下列方法：

    - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

    - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

    - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

    - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

    - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

    - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

     提供了 SDM attach 和 detach 本身的處理程序的方式。

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

     描述邏輯的程式。 至少必須實作下列方法：

    - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

    - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

    - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

     提供了 SDM 附加至這個程式的方式。

## <a name="see-also"></a>另請參閱
- [實作連接埠提供者](../../extensibility/debugger/implementing-a-port-supplier.md)