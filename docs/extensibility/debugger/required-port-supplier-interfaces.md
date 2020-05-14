---
title: 所需的埠供應商介面 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713156"
---
# <a name="required-port-supplier-interfaces"></a>所需的連接埠供應商介面
埠供應商必須實現[IDebugPort 供應商2](../../extensibility/debugger/reference/idebugportsupplier2.md)介面。[IDebugPort供應商2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 埠供應商提供埠並實現它們。 因此,它必須運行以下介面:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  描述埠並枚舉在埠上運行的所有進程。

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  提供在埠上啟動和終止進程。

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  為在此埠上下文中運行的程式提供一種機制,以通知其程式節點的創建和銷毀。 有關詳細資訊,請參閱[程式節點](../../extensibility/debugger/program-nodes.md)。

- `IConnectionPointContainer`

  為[IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)提供連接點。

## <a name="port-supplier-operation"></a>港口供應商運營
 在埠上創建和銷毀進程和程式時[,IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)接收器會接收通知。 創建行程時需要埠發送[IDebugProcessCreateEvent2;](../../extensibility/debugger/reference/idebugprocesscreateevent2.md)在埠上銷毀進程時,需要[IDebugProcessCreateEvent2。](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) 創建程式時,還需要埠發送[IDebugProgramCreateEvent2;](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)在埠上運行的進程中銷毀程式時,需要[發送 IDebugProgramCreateEvent2。](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

 埠通常分別發送程式創建和銷毀事件以回應[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)和[RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法。

 由於埠可以啟動和終止物理進程和邏輯程式,因此調試引擎還必須實現以下介面:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  描述物理過程。 至少必須實現以下方法:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [取得行程 Id](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  為 SDM 提供一種從進程中附加和分離自身的方法。

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  描述邏輯程式。 至少必須實現以下方法:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [抓取程序](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  為 SDM 提供了一種附加到此程式的方法。

## <a name="see-also"></a>另請參閱
- [實施埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)
