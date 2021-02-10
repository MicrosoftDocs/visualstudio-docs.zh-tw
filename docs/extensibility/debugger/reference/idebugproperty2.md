---
title: IDebugProperty2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c5cec0d93919058eae725a9e49198f1704d8bfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962193"
---
# <a name="idebugproperty2"></a>IDebugProperty2
這個介面代表堆疊框架屬性、程式檔案屬性或其他屬性。 屬性通常是運算式評估的結果。

> [!NOTE]
> 雖然可以表示這類實體，但不應該將「屬性」的用法與表示類別的成員變數混淆 `IDebugProperty2` 。

## <a name="syntax"></a>Syntax

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面以表示特定種類的值。 例如，值可能是運算式評估的結果、用來顯示記憶體的記憶體內容，或是暫存器清單及其值的數值。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 來取得這個介面，此介面代表評估的結果。 `IDebugExpression2::EvaluateAsync` 藉由將 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 介面傳送至 SDM 來傳回這個介面，後者接著會呼叫 [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 來抓取屬性。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) 會傳回這個介面，以提供相關聯的指令檔。

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) 會傳回這個介面，以代表函數的傳回值。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) 會傳回這個介面，以代表程式的各種屬性，例如名稱或記憶體內容。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 會傳回這個介面，以代表堆疊框架的各種屬性，例如區域變數。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProperty2` 。

|方法|描述|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|填入描述屬性的 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構。|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|從字串設定屬性的值。|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|從指定的參考值設定屬性的值。|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|列舉屬性的子系。|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|傳回屬性的父系。|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|傳回描述屬性之最高衍生屬性的屬性。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|傳回組成屬性值的記憶體位元組。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|傳回屬性值的記憶體內容。|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|傳回屬性值的大小（以位元組為單位）。|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|傳回這個屬性值的參考。|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|傳回屬性的擴充資訊。|

## <a name="remarks"></a>備註
 以介面表示的屬性， `IDebugProperty2` 可以視為具有名稱、類型和位址值的值。 在更一般的詞彙中， `IDebugProperty2` 可以使用父節點和子節點來代表具有階層式結構的任何事物。

 屬性通常是暫時性的，只有在目前的堆疊框架（例如）的情況下才會持續。 另一方面， [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 介面所代表的參考，只要值仍在記憶體中，就會持續。

 IDE 可以使用 `IDebugProperty2` 介面，讓使用者在執行時間流覽和修改屬性。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
