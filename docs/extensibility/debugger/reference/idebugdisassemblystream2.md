---
title: IDebugDisassemblyStream2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf91235b1321b13571505c51af077643c606c4a7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310303"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
這個介面會表示指令資料流。

## <a name="syntax"></a>語法

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎會實作這個介面，以支援反組譯碼的程式碼。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法會傳回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugDisassemblyStream2`。

|方法|描述|
|------------|-----------------|
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|讀取從目前的位置，在反組譯碼資料流中的指示。|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|反組譯碼資料流指定數目的相對於指定位置的指示中移動讀取的指標。|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|傳回特定的程式碼內容的程式碼位置識別碼。|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|傳回對應至指定的程式碼位置識別碼的程式碼內容物件。|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|傳回代表目前的程式碼位置的程式碼位置識別碼。|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|取得與這個反組譯碼資料流相關聯的來源文件。|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|取得這個反組譯碼資料流的範圍。|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|取得這個反組譯碼資料流的大小。|

## <a name="remarks"></a>備註
 反組譯碼資料流可以建立來代表整個位址空間只函式或模組內的空間。 表示每個指令[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)呼叫所傳回的結構[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)