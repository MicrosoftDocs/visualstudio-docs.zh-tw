---
description: Debug engine (DE) 會使用此介面來要求載入檔。
title: IDebugActivateDocumentEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbf24620b3dfa508a52463598219be4b2d7439a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094392"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Debug engine (DE) 會使用此介面來要求載入檔。

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 當這個介面需要開啟來源檔案時，就會執行這個介面。 這個介面只會由使用或屬於腳本解譯器一部分的偵錯工具引擎來執行。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 使用[QueryInterface](/cpp/atl/queryinterface)來存取 `IDebugEvent2` 介面) 。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當它需要開啟來源檔案時，會建立並傳送此事件物件。 當附加至要進行偵錯工具的程式時，會使用由 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugActivateDocumentEvent2` 。

|方法|描述|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|取得要啟動的檔。|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|取得描述檔中位置的檔內容。|

## <a name="remarks"></a>備註
 使用這個介面的一般案例是，如果在 HTML 網頁的腳本程式碼中發生剖析錯誤，腳本會將這個介面傳送給 SDM，以便顯示具有剖析錯誤的檔。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
