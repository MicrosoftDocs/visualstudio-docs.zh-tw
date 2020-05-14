---
title: IDebug記憶位元組2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727513"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
此介面表示記憶體的位元組數。

## <a name="syntax"></a>語法

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示記憶體中的位元組。

## <a name="notes-for-callers"></a>通話備註
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)傳回此介面以提供對系統記憶體的訪問。 [獲取記憶體位元組](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)和[獲取記憶體位元組](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)返回此介面以提供對物件的位元組的訪問。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugMemoryBytes2`。

|方法|描述|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|從給定位置開始讀取位元組序列。|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|寫入`dwCount`位元組`pStartContext`,從開始。|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|獲取此介面表示的記憶體的大小(以位元組為單位)。|

## <a name="remarks"></a>備註
 對於屬性,表示陣列的[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面提供了`IDebugMemoryBytes2`一個介面來訪問該陣列中的值。

 Visual Studio 的**記憶體檢視**調用[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)`IDebugMemoryBytes2`來檢索用於存取系統記憶體的介面。 要造訪的位址是透過分析以位址輸入到記憶體檢視中的運算式,然後使用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)運算解析的表示式來`IDebugProperty2`獲取介面。 對[GetMemoryContext 的](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)呼叫傳回描述記憶體位址的[IDebugMemoryContext2。](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 然後,此記憶體上下文將傳遞到[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)和[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
