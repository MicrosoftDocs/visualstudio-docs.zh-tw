---
title: IDebugProcess3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723539"
---
# <a name="idebugprocess3"></a>IDebugProcess3
此介面表示正在運行的進程及其程式。 此介面作為[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面中多種方法的替換而存在。 它提供對流程中所有程式的控制。

> [!NOTE]
> [將棄用"繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)["、執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)和[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)方法,不應再使用。 而是在`IDebugProcess3`介面上使用相應的方法。

## <a name="syntax"></a>語法

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由自定義埠供應商實現,以作為一個組管理程式。 當程式作為一個組進行管理時,您可以控制其執行併為表達式賦值器建立語言。 此介面必須由埠供應商實現。

## <a name="notes-for-callers"></a>通話備註
 此介面主要由工作階段調試管理員 (SDM) 調用,以便與在此過程中識別的一組程式進行互動。

 在[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)繼承的方法`IDebugProcess3`外, 還實現了以下方法。

|方法|描述|
|------------|-----------------|
|[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|繼續執行或逐步執行流程。|
|[執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|開始執行進程。|
|[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)|在此過程中向前走一條指令或語句。|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|獲取進程啟動以進行調試的原因。|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|設置託管語言,以便調試引擎可以載入相應的運算式賦值器。|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|檢索當前為此過程設置的語言。|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|禁用此過程的編輯並繼續 (ENC)。<br /><br /> 自定義埠供應商不實現此方法(應始終返回`E_NOTIMPL`)。|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|獲取此過程的 ENC 狀態。<br /><br /> 自定義埠供應商不實現此方法(應始終返回`E_NOTIMPL`)。|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|檢索可用調試引擎的唯一標識符陣列。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
