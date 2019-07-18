---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd50186abbf94ae294c346a5981bee14f45820fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317098"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
這個介面會列舉在目前的偵錯工作階段中執行的程式。

## <a name="syntax"></a>語法

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面可提供一份由 DE 偵錯的程式。

## <a name="notes-for-callers"></a>呼叫端資訊
 Visual Studio 呼叫[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)來取得這個介面。 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)不是由 Visual Studio。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugPrograms2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|擷取指定的數目的列舉型別序列中的程式。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|略過指定的數目的列舉型別序列中的程式。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|將列舉型別序列重設到開頭。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|取得列舉值中的程式數目。|

## <a name="remarks"></a>備註
 Visual Studio 會使用此介面，以便：

- 填入**模組** 視窗 (透過呼叫[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ，然後再呼叫[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)上每個程式)。

- 填入**připojit k procesu**清單中 (藉由呼叫`IDebugProcess2::EnumPrograms`然後呼叫[QueryInterface](/cpp/atl/queryinterface)每個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面，以取得[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)介面)。

- 產生一份可以偵錯程序中的每個程式的 DEs (使用[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md))。

- 將編輯後繼續 (ENC) 更新套用至每個程式 (透過呼叫 IDebugProcess2::EnumPrograms 並接著呼叫[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md))。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)