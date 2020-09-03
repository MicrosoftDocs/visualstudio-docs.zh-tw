---
title: IDebugProviderProgramNode2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720676"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
此介面會跨進程界限封送處理常式相關的介面。

## <a name="syntax"></a>語法

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會在執行 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 的相同物件上執行這個介面，以支援跨進程界限的封送處理介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` 來取得這個介面。 如果無法取得這個介面，則不支援對介面進行封送處理。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|取得跨進程界限的指定介面。|

## <a name="remarks"></a>備註
 此介面會在從正在進行偵錯工具的不同進程空間中執行時執行：例如，在 Visual Studio 的進程空間中執行取消作業，而非正在進行偵錯工具的進程空間時。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
