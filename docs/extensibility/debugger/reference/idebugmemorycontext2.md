---
title: IDebug記憶體上下文2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727423"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
此介面表示運行正在調試的程式的計算機的位址空間中的位置。

## <a name="syntax"></a>語法

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示記憶體中的位址。

## <a name="notes-for-callers"></a>通話備註
 對[獲取記憶體上下文](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)或[獲取記憶體上下文](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)的調用將返回此介面。 此外,在應用適當的算術運算後,對[「添加](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)[」和「減法」](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)的調用將返回此介面的新副本。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugMemoryContext2`。

|方法|描述|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|獲取此上下文的用戶可顯示名稱。|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|獲取描述此上下文的資訊。|
|[加入](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|將指定值添加到當前上下文的位址以創建新上下文。|
|[減去](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|從當前上下文的位址中減去指定值以創建新上下文。|
|[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|以比較標誌指示的方式比較兩個上下文。|

## <a name="remarks"></a>備註
 Visual Studio 的**記憶體**視窗呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)`IDebugMemoryContext2`以取得包含用於記憶體地址的計算表達式的介面。 然後,此上下文將傳遞到[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)和[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)以指定要讀取或寫入的位址。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
