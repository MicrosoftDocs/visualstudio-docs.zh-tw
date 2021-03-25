---
description: 此介面代表位元組的記憶體。
title: IDebugMemoryBytes2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b18b4575780966d9ad34fa6c5638a89274d52c3c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058634"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
此介面代表位元組的記憶體。

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行此介面來代表記憶體中的位元組。

## <a name="notes-for-callers"></a>呼叫者注意事項
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 會傳回這個介面，以提供系統記憶體的存取權。 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 和 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) 會傳回這個介面，以提供物件位元組的存取權。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugMemoryBytes2` 。

|方法|描述|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|從指定位置開始讀取一連串的位元組。|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|寫入 `dwCount` 位元組，從開始 `pStartContext` 。|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|取得由此介面表示之記憶體的大小（以位元組為單位）。|

## <a name="remarks"></a>備註
 若為屬性，代表陣列的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 介面會提供 `IDebugMemoryBytes2` 介面來存取該陣列中的值。

 Visual Studio 的 **記憶體 View** 呼叫 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) 來取得 `IDebugMemoryBytes2` 存取系統記憶體的介面。 要存取的位址是藉由將輸入為位址的運算式剖析至記憶體視圖，然後使用 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 來取得介面來評估剖析的運算式而取得 `IDebugProperty2` 。 呼叫 [GetMemoryCoNtext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) 會傳回描述記憶體位址的 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 。 此記憶體內容接著會傳遞至 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) 和 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
