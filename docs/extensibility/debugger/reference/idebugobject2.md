---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3f027fd08c38433d5f1357e56d90df96e223854
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317255"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面會提供物件的其他資訊。

## <a name="syntax"></a>語法

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具會實作這個介面來提供支援的別名以及存取物件的相關資訊。

## <a name="notes-for-callers"></a>呼叫端資訊
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用，取得這個介面[QueryInterface](/cpp/atl/queryinterface)。 此外， [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)傳回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 上的方法除了[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面，`IDebugObject2`實作下列介面：

|方法|描述|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|取得變數的欄位 （如果有的話），可能會支援這個物件所表示的屬性。|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|取得表示這個物件值的 managed 程式碼物件。|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|建立此物件的唯一識別碼，或傳回現有的別名。|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|如果有的話，請取得與這個物件相關聯的別名。|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|取得這個物件的型別。|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|判斷這個物件是否代表使用者資料。|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|判斷是否不再有效的編輯後繼續的狀態。<br /><br /> 自訂運算式評估工具不會實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|

## <a name="remarks"></a>備註
 請參閱[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)如需別名的討論。

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)