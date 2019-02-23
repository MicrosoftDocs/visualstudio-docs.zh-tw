---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 979ca1b0422cf3a333164570aec0a0b0dee39960
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693642"
---
# <a name="idebugprocess3"></a>IDebugProcess3
這個介面會表示執行中處理序和其程式。 這個介面是否存在，在數種方法來取代[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。 它可讓控制程序中的所有程式。

> [!NOTE]
>  [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)， [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)，以及[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)方法已被取代，並且無法再使用。 使用上的對應方法`IDebugProcess3`改為介面。

## <a name="syntax"></a>語法

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>實作者的附註
 若要以群組方式管理程式的自訂連接埠供應商提供的被實作這個介面。 當程式以群組進行管理時，您可以控制其執行，並建立一種語言的運算式評估工具。 透過連接埠提供者，就必須實作這個介面。

## <a name="notes-for-callers"></a>呼叫端資訊
 此介面稱為主要是由工作階段的偵錯管理員 (SDM) 來進行互動的程式識別在這個程序中的群組。

 呼叫[QueryInterface](/cpp/atl/queryinterface)上[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)介面，以取得此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自方法[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)，`IDebugProcess3`實作下列方法。

|方法|描述|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|會持續執行，或是逐步執行程序。|
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|開始執行的處理序。|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|步驟轉送一指令或處理序中的陳述式。|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|取得處理序已啟動的偵錯的原因。|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|設定主機的語言，以便偵錯引擎可以載入適當的運算式評估工具。|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|擷取目前針對此程序設定的語言。|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|此程序，停用編輯後繼續 (ENC)。<br /><br /> 自訂連接埠供應商不會實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|取得這個處理程序的 ENC 狀態。<br /><br /> 自訂連接埠供應商不會實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|擷取可用的偵錯引擎的唯一識別碼的陣列。|

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)