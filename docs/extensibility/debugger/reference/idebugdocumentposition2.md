---
title: IDebug文檔位置2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731645"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
此介面表示源檔中的抽象位置。

## <a name="syntax"></a>語法

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 可視化工作室通常實現此介面。 除錯引擎 (DE) 如果必須提供自己的原始碼(就像 DE 實現[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面時一樣),它也將實現此介面。

## <a name="notes-for-callers"></a>通話備註
 此介面作為參數傳遞給[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)。 它還作為[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)聯合(特別是[BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)結構)的一部分提供,該聯合是[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構的一部分,用於創建掛起的斷點。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugDocumentPosition2`。

|方法|描述|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|獲取包含此文件位置的源檔的檔名。|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|獲取包含的文檔。|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|確定此位置是否包含在給定文件中。|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|獲取此文件位置的範圍。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
