---
title: IDebugActivate文檔事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736613"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
除錯引擎 (DE) 使用此介面請求載入文件。

## <a name="syntax"></a>語法

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 當 DE 需要打開源檔時,它實現此介面。 此介面僅通過使用腳本解釋器或腳本解釋器的一部分的調試引擎實現。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

## <a name="notes-for-callers"></a>通話備註
 當 DE 需要打開源檔時,它將創建併發送此事件物件。 該事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugActivateDocumentEvent2`。

|方法|描述|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|獲取要啟動的文檔。|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|獲取描述文件中位置的文檔上下文。|

## <a name="remarks"></a>備註
 使用此介面的典型方案是,如果 HTML 頁上的文本代碼中出現分析錯誤,文本 DE 會將此介面發送到 SDM,以便顯示具有分析錯誤的文檔。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
