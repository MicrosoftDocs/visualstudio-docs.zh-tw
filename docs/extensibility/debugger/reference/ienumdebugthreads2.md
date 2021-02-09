---
title: IEnumDebugThreads2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e3771545d4a5fe545382344d17ed5ea929999d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852774"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
這個介面會列舉在目前的 debug 會話中執行的執行緒。

## <a name="syntax"></a>Syntax

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表程式中的執行緒清單。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) 以取得這個介面，此介面代表在進程中執行之所有程式的所有線程清單。 呼叫 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 以取得這個介面，此介面代表在程式中執行的執行緒清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugThreads2` 。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|抓取列舉序列中指定數目的執行緒。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|略過列舉序列中指定數目的執行緒。|
|[重設](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|建立列舉值，其中包含與目前相同的列舉狀態。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|取得列舉值中的執行緒數目。|

## <a name="remarks"></a>備註
 Visual Studio 通常會取得此介面來更新 [ **執行緒** ] 視窗，以及取得清單的第一個執行緒，以便呼叫 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)、 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)和 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
