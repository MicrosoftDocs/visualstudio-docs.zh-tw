---
title: IDebug屬性2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721232"
---
# <a name="idebugproperty2"></a>IDebugProperty2
此介面表示堆疊幀屬性、程序文檔屬性或其他屬性。 該屬性通常是表達式計算的結果。

> [!NOTE]
> 不應將"屬性"的這種使用與類的成員變數的含義混淆,儘管 可以`IDebugProperty2`表示此類實體。

## <a name="syntax"></a>語法

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以表示特定類型的值。 例如,該值可以是表達式計算的結果、用於顯示記憶體的記憶體上下文或寄存器及其值的清單。

## <a name="notes-for-callers"></a>通話備註
 調用[評估同步](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)[或評估同步](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)以獲取此介面,該介面表示評估的結果。 `IDebugExpression2::EvaluateAsync`通過向 SDM 發送[IDebugExpression Expression評估完成事件2 介面](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)來返回此介面,SDM 又調用[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)來檢索該屬性。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)返回此介面以提供關聯的腳本文檔。

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)返回此介面以表示函數的返回值。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)返回此介面以表示程式的各種屬性,如名稱或記憶體上下文。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)返回此介面以表示堆疊幀的各種屬性,如局部變數。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProperty2`。

|方法|描述|
|------------|-----------------|
|[取得財產資訊](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|填寫描述屬性[的DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|從字串設定屬性的值。|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|從給定引用的值設置屬性的值。|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|枚舉屬性的子級。|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|返回屬性的父級。|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|返回描述屬性最派生屬性的屬性。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|返回組成屬性值的記憶體位元組。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|返回屬性值的記憶體上下文。|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|返回屬性值的大小(以位元組為單位)。|
|[取得參考](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|返回對此屬性值的引用。|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|返回屬性的擴展資訊。|

## <a name="remarks"></a>備註
 屬性(由`IDebugProperty2`介面表示)可以視為具有名稱、類型和位址的值。 更籠統地說,`IDebugProperty2`可以表示具有層次結構的任何內容,以及父節點和子節點。

 屬性通常是短暫的,僅持續於當前堆疊幀(例如)。 另一方面,引用(由[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面表示)只要該值保留在記憶體中,該引用就持續。

 IDE 可以使用`IDebugProperty2`該 介面允許使用者在運行時流覽和修改屬性。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
