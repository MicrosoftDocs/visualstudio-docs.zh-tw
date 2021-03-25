---
description: 此介面代表來源文件。
title: IDebugDocument2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b84aa99e1f09bc50c2148b7e03fab9e2a5bb5814
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066837"
---
# <a name="idebugdocument2"></a>IDebugDocument2
此介面代表來源文件。

## <a name="syntax"></a>Syntax

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 通常會執行這個介面。 當它需要提供原始程式碼且來源不存在於磁片上時，debug engine (DE) 也可以執行這個介面。  在這種情況下，DE 也會執行 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 和 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) 介面，以及 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 和 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 介面上的一些其他方法。

## <a name="notes-for-callers"></a>呼叫者注意事項
 、、和介面上的方法會傳回 `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` `IDebugActivateDocumentEvent2` 這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugDocument2` 。

|方法|描述|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|以數種形式的其中一種取得檔的名稱。|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|取得檔的類別識別碼。|

## <a name="remarks"></a>備註
 只有在取消提供原始程式碼時，才會執行這個介面。 例如，當您在 HTML 網頁上對腳本進行偵錯工具時，會因為來源是以動態方式下載或產生，而不是以磁片檔案的形式存在，所以會提供原始程式碼。 在對傳統語言（例如 c + +）進行偵測時，不需要執行這個介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
