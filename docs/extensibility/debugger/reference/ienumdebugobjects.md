---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dea4b4781fd8026c29436bbd37a6bfa6824e73b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339488"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面代表實作的物件的集合[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面。

## <a name="syntax"></a>語法

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具會實作這個介面來提供實作的物件的集合[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面。 請注意，這不是標準的 COM 列舉的緣故[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)方法。

## <a name="notes-for-callers"></a>呼叫端資訊
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)傳回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 這個介面會實作下列方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|擷取下的一組[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)列舉中的物件。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|略過指定的數目的項目。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|將列舉重設第一個項目中。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|擷取一份目前的列舉型別。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|擷取列舉中的項目數。|

## <a name="remarks"></a>備註
 這個介面允許列舉一組物件陣列中的偵錯引擎。

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)