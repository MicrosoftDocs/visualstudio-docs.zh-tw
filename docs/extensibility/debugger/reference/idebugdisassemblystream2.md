---
title: IDebugdisassembly2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732040"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
此介面表示指令流。

## <a name="syntax"></a>語法

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎實現此介面以支援程式代碼的拆解。

## <a name="notes-for-callers"></a>通話備註
 對[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法的調用將返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugDisassemblyStream2`。

|方法|描述|
|------------|-----------------|
|[讀](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|讀取從拆解流中的當前位置開始的指令。|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|相對於指定位置,在拆解流中移動讀取指標的給定指令數。|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|返回特定代碼上下文的代碼位置識別碼。|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|返回與指定代碼位置識別碼內容的程式碼上下文物件。|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|返回表示目前代碼位置的代碼位置識別碼。|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|獲取與此拆解流關聯的源文檔。|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|獲取此拆解流的範圍。|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|獲取此拆解流的大小。|

## <a name="remarks"></a>備註
 可以創建拆解流以表示整個位址空間,或者僅表示空間內的函數或模組。 每個指令都由對[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法的調用返回的[拆解數據](../../../extensibility/debugger/reference/disassemblydata.md)結構表示。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
