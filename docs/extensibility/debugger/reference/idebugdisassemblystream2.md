---
description: 此介面代表指示的資料流程。
title: IDebugDisassemblyStream2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 760d77ced3cc07da2dd02c21cf3ed0200df14231
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166563"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
此介面代表指示的資料流程。

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 偵錯工具引擎會執行這個介面，以支援程式碼的反組譯。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 方法會傳回這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugDisassemblyStream2` 。

|方法|描述|
|------------|-----------------|
|[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|從反組解碼資料流程中的目前位置開始讀取指示。|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|移動反組解碼資料流程中的讀取指標，指定的指示數目相對於指定的位置。|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|傳回特定程式碼內容的程式碼位置識別碼。|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|傳回對應至指定之程式碼位置識別碼的程式碼內容物件。|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|傳回代表目前程式碼位置的程式碼位置識別碼。|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|取得與此反組解碼資料流程相關聯的來源文件。|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|取得此反組解碼資料流程的範圍。|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|取得此反組解碼資料流程的大小。|

## <a name="remarks"></a>備註
 您可以建立反組解碼資料流程來代表整個位址空間，或只是空間內的函式或模組。 每個指令都是由對[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法的呼叫所傳回的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構來表示。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
