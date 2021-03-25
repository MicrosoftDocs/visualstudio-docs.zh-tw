---
description: 這個介面代表特定執行緒中呼叫堆疊內的單一堆疊框架。
title: IDebugStackFrame2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9675627bf3044258a532ca91768619f2c6de3ba
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053252"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
這個介面代表特定執行緒中呼叫堆疊內的單一堆疊框架。

## <a name="syntax"></a>Syntax

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行此介面來代表堆疊框架。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 以取得 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 介面。 呼叫 [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) 以取得包含介面的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構 `IDebugStackFrame2` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugStackFrame2` 。

|方法|描述|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|取得這個堆疊框架的程式碼內容。|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|取得這個堆疊框架的檔內容。|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|取得堆疊框架的名稱。|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|取得堆疊框架的描述。|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|取得與堆疊框架相關聯之實體位址範圍的電腦相依標記法。|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|取得評估內容，以在堆疊框架和執行緒的目前內容中進行運算式評估。|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|取得與堆疊框架相關聯的語言。|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|取得與堆疊框架相關聯之屬性的描述。|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|建立堆疊框架屬性的列舉值。|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|取得與堆疊框架相關聯的執行緒。|

## <a name="remarks"></a>備註
 只有在正在進行偵錯工具的中斷點停止時，才會取得這個介面 (可能是使用者設定中斷點或例外狀況) 所造成。 您可以從這個介面取得運算式內容來評估運算式、可以傳回暫存器清單，或者可以取得和檢查呼叫堆疊。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
