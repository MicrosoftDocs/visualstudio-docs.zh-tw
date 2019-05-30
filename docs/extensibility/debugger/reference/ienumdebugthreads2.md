---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6d8f869e519d9500f1ea8f3bb33a3ee098f5cfd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325410"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
這個介面會列舉在目前的偵錯工作階段中執行的執行緒。

## <a name="syntax"></a>語法

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面來代表清單的程式中的執行緒。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)來取得這個介面，表示處理序中執行的所有程式 中的所有執行緒的清單。 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)來取得這個介面，表示在程式中執行的執行緒清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugThreads2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|擷取指定的列舉型別序列中的執行緒數目。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|略過指定的列舉順序中的執行緒數目。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|將列舉型別序列重設到開頭。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|建立包含相同的列舉型別目前狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|取得列舉值中的執行緒數目。|

## <a name="remarks"></a>備註
 Visual Studio 通常會取得這個介面來更新**執行緒**以及對於取得的第一個執行緒的清單中，若要呼叫的視窗[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)，[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)，及[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
