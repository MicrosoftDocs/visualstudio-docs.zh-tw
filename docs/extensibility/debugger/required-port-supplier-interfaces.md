---
title: 必要的埠提供者介面 |Microsoft Docs
description: 瞭解埠供應商必須執行的介面。 埠供應商會提供埠並加以實行。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 13e3ac8dc0c229f0c0a00bd22131251c71893224
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847126"
---
# <a name="required-port-supplier-interfaces"></a>必要的埠提供者介面
埠供應商必須執行 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 介面。[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 埠供應商會提供埠並加以實行。 因此，它必須執行下列介面：

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  描述埠，並列舉在埠上執行的所有進程。

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  提供在埠上啟動和終止進程的。

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  提供在此埠內容中執行之程式的機制，以在建立和終結程式節點時通知它。 如需詳細資訊，請參閱 [程式節點](../../extensibility/debugger/program-nodes.md)。

- `IConnectionPointContainer`

  提供 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)的連接點。

## <a name="port-supplier-operation"></a>埠供應商操作
 當進程和程式在埠上建立和終結時， [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) 接收就會收到通知。 建立進程時必須要有埠才能傳送 [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) ，並在埠上終結進程時進行 [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) 。 建立程式時，也需要端口來傳送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ，並在埠上執行的進程終結程式時進行 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 。

 埠通常會分別傳送程式建立和終結事件，以回應 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 和 [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) 方法。

 由於埠可以啟動和終止實體處理常式和邏輯程式，因此，debug 引擎也必須執行下列介面：

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  描述實體處理常式。 至少必須執行下列方法：

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  提供一種方式，讓 SDM 從進程附加和卸離本身。

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  描述邏輯程式。 至少必須執行下列方法：

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  提供方法讓 SDM 附加至此程式。

## <a name="see-also"></a>另請參閱
- [執行埠供應商](../../extensibility/debugger/implementing-a-port-supplier.md)
