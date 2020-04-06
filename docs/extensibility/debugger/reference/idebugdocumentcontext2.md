---
title: IDebug文檔上下文2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731739"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
此介面表示源文件文件中的位置。

## <a name="syntax"></a>語法

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其支援原始碼級調試的一部分。 除了原始碼中的位置外,此介面還提供用於比較上下文和流覽原始程式碼文件的方法。

## <a name="notes-for-callers"></a>通話備註
 多個介面(通常為[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)和[GetDocumentContext)](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)介面上的方法返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugDocumentContext2`。

|方法|描述|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|獲取包含此文件上下文的文檔。|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|獲取包含此文件上下文的文件的可顯示名稱。|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|檢索與此文檔上下文關聯的所有代碼上下文的清單。|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|獲取與此文件上下文關聯的語言。|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|獲取此文件上下文的檔語句範圍。|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|獲取此文件上下文的檔源範圍。|
|[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|將此文件上下文與給定的文檔上下文陣列進行比較。|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|按給定數量的語句或行移動文檔上下文。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
