---
title: IEnum調試線程2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715093"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
此介面枚舉在當前調試會話中運行的線程。

## <a name="syntax"></a>語法

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示程式中的線程清單。

## <a name="notes-for-callers"></a>通話備註
 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)以取得此介面,以表示行程中執行的所有程式中所有線程的清單。 呼叫[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)以獲取此介面,表示程式中正在執行的線程清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugThreads2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|檢索枚舉序列中指定數量的線程。|
|[跳](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|在枚舉序列中跳過指定數量的線程。|
|[重設](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|創建與當前枚舉狀態相同的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|獲取枚舉器中的線程數。|

## <a name="remarks"></a>備註
 Visual Studio 通常取得此介面以更新**執行緒**視窗, 以及取得清單的第一個線程,以便[呼叫、](../../../extensibility/debugger/reference/idebugprocess3-execute.md)[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)與[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
