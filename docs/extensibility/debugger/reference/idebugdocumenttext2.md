---
description: 此介面代表文字檔。
title: IDebugDocumentText2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1c5928362616466985a6f88102ffcbf4377444
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154206"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
此介面代表文字檔。

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 當需要提供的原始程式碼是文字格式時，debug engine (DE) 會執行這個介面。 由於這是最常見的情況，因此，如果 DE 會執行 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 介面，它也應該實作為 `IDebugDocumentText2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 您 `QueryInterface` 可以使用方法，從介面取得這個介面 `IDebugDocument2` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了介面上的方法 `IDebugDocument2` ，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|抓取檔中這個位置的文字大小。|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|從檔中指定的位置抓取文字。|

## <a name="remarks"></a>備註
 實此介面的物件也必須執行 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 介面，以提供 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) 物件的介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
