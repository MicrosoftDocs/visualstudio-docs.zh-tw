---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43b03a7b26af76d5d914e1aa3ef182d18c805f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873249"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
此介面代表記憶體位元組。

## <a name="syntax"></a>語法

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面來代表記憶體中的位元組。

## <a name="notes-for-callers"></a>呼叫端資訊
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)傳回此介面，以提供系統記憶體的存取權。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)並[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)傳回此介面，以提供存取物件的位元組。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugMemoryBytes2`。

|方法|描述|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|讀取指定的位置開始的位元組序列。|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|寫入`dwCount`開始的位元組`pStartContext`。|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|取得大小，以位元組為單位，此介面所代表的記憶體。|

## <a name="remarks"></a>備註
 屬性，如[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面，表示陣列提供`IDebugMemoryBytes2`介面，以存取該陣列中的值。

 Visual Studio**記憶體檢視**呼叫[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)擷取`IDebugMemoryBytes2`介面來存取系統記憶體。 取得要存取位址剖析為位址輸入到記憶體的檢視運算式，然後再評估 剖析的運算式使用[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)若要取得`IDebugProperty2`介面。 呼叫[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)會傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)描述的記憶體位址。 此記憶體內容會傳遞至[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)並[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)