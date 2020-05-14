---
title: IDebugStackFrame2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719505"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
此介面表示特定線程中的調用堆疊中的單個堆疊幀。

## <a name="syntax"></a>語法

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 調試引擎 (DE) 實現此介面以表示堆疊幀。

## <a name="notes-for-callers"></a>通話備註
 呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)以檢索[IEnum DebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)介面。 調用[下一個](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)以檢索包含`IDebugStackFrame2`介面的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugStackFrame2`。

|方法|描述|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|獲取此堆疊幀的代碼上下文。|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|獲取此堆疊框架的文檔上下文。|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|獲取堆疊幀的名稱。|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|獲取堆疊幀的說明。|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|獲取與堆疊幀關聯的物理地址範圍的與計算機相關的表示形式。|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|獲取用於在堆疊框架和線程的當前上下文中執行表達式計算的評估上下文。|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|獲取與堆疊幀關聯的語言。|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|獲取與堆疊幀關聯的屬性的說明。|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|為堆疊幀屬性創建枚舉器。|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|獲取與堆疊幀關聯的線程。|

## <a name="remarks"></a>備註
 僅當正在調試的程式在斷點(由用戶設置的斷點或異常引起)停止時,才獲得此介面。 在此介面中,可以獲取表達式上下文以評估表達式,可以返回寄存器清單,也可以獲取和檢查調用堆疊。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
