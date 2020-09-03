---
title: IDebugMemoryCoNtext2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727423"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
此介面代表執行正在進行偵錯工具之電腦的位址空間中的位置。

## <a name="syntax"></a>語法

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行此介面來代表記憶體中的位址。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [GetMemoryCoNtext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 或 [GetMemoryCoNtext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) 的呼叫會傳回這個介面。 此外，在套用適當的算數運算之後，對 [加入](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) 和 [減去](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) 的呼叫會傳回這個介面的新複本。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugMemoryContext2` 。

|方法|描述|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|取得此內容的使用者可顯示名稱。|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|取得描述此內容的資訊。|
|[加入](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|將指定的值加入至目前內容的位址，以建立新的內容。|
|[減去](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|從目前內容的位址減去指定的值，以建立新的內容。|
|[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|比較旗標所指定的方式來比較兩個內容。|

## <a name="remarks"></a>備註
 Visual Studio 的 [ **記憶體** ] 視窗會呼叫 [GetMemoryCoNtext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ，以取得 `IDebugMemoryContext2` 包含用於記憶體位址之評估運算式的介面。 此內容接著會傳遞至 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 和 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) ，以指定要讀取或寫入的位址。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
