---
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef390f3f67a0c0678854020e33725b2f88439ff9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308911"
---
# <a name="idebugproperty2"></a>IDebugProperty2
此介面代表堆疊框架屬性、 程式文件屬性或某些其他屬性。 屬性通常是運算式評估的結果。

> [!NOTE]
> 這種使用 「 屬性 」 不應混淆與表示類別的成員變數雖然`IDebugProperty2`可以表示這個實體。

## <a name="syntax"></a>語法

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 會實作這個介面來代表特定類型的值。 例如，值可以是數值，運算式評估，用來顯示記憶體或暫存器和其值的清單的記憶體內容的結果。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或是[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)來取得這個介面，表示評估的結果。 `IDebugExpression2::EvaluateAsync` 傳回此介面傳送[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) SDM，而呼叫的介面[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)來擷取屬性。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)傳回這個介面來提供相關聯的指令碼文件。

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)傳回這個介面來表示函式的傳回值。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)傳回這個介面來代表不同的屬性，例如名稱或記憶體內容的程式。

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)傳回這個介面來代表堆疊框架，例如區域變數的各種屬性。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProperty2`。

|方法|描述|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|填寫[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構描述的屬性。|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|從字串中設定屬性的值。|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|從指定參考的值設定屬性的值。|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|列舉屬性的子系。|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|傳回屬性的父代。|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|傳回描述屬性的最高衍生性屬性的屬性。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|傳回組成屬性值的記憶體位元組。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|傳回屬性值的記憶體內容。|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|傳回大小，以位元組為單位的屬性值。|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|傳回這個屬性的值的參考。|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|傳回屬性的擴充的資訊。|

## <a name="remarks"></a>備註
 屬性表示的`IDebugProperty2`介面中，可以視為具有名稱、 類型和地址的值。 在較籠統的字詞，`IDebugProperty2`可以代表任何項目都具有包含父代和子節點的階層式結構。

 通常是暫時性的例如只有在目前的堆疊框架上，為持續的屬性。 另一方面，參考，表示所[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面，會持續，只要保留在記憶體中的值。

 可以使用 IDE`IDebugProperty2`介面，可讓使用者瀏覽及修改屬性，在執行階段。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)