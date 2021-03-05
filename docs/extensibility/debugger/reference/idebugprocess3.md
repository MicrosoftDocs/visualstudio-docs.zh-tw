---
description: 此介面代表執行中的進程及其程式。
title: IDebugProcess3 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2303dfef18a1abccc728d80def0de25b4e7eadd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169180"
---
# <a name="idebugprocess3"></a>IDebugProcess3
此介面代表執行中的進程及其程式。 這個介面是取代為 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面中的數個方法。 它可讓您控制進程中的所有程式。

> [!NOTE]
> [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)、 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)和 [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) 方法已被取代，不應該再使用。 請改為在介面上使用對應的方法 `IDebugProcess3` 。

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由自訂埠供應商所執行，以群組的方式來管理程式。 當程式以群組方式管理時，您可以控制其執行，並建立運算式評估工具的語言。 此介面必須由埠供應商來執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面主要是由會話 debug manager (SDM) 所呼叫，以便與此程式中所識別的程式群組進行互動。

 呼叫[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面上的[QueryInterface](/cpp/atl/queryinterface)來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)的方法之外，還會執行 `IDebugProcess3` 下列方法。

|方法|描述|
|------------|-----------------|
|[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|繼續執行或逐步執行進程。|
|[執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|開始執行進程。|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|在程式中向前復原一個指令或語句。|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|取得啟動處理常式以進行偵錯工具的原因。|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|設定裝載語言，讓 debug engine 可以載入適當的運算式評估工具。|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|抓取目前為此進程設定的語言。|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|停用此進程 (ENC) 的 [編輯後繼續]。<br /><br /> 自訂埠供應商不會執行此方法 (它應該一律傳回 `E_NOTIMPL`) 。|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|取得此進程的 ENC 狀態。<br /><br /> 自訂埠供應商不會執行此方法 (它應該一律傳回 `E_NOTIMPL`) 。|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|抓取可用之偵錯工具引擎的唯一識別碼陣列。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
