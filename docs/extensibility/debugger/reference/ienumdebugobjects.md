---
title: IEnumDebugObjects |Microsoft Docs
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
ms.openlocfilehash: 749b3faf938fbc862fdf9b406127c898ee6b6d98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727568"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方式已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱[Clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)工具和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面代表用來執行[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面的物件集合。

## <a name="syntax"></a>語法

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行此介面，以提供可實[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面的物件集合。 請注意，這不是標準的 COM 列舉，因為[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)方法存在。

## <a name="notes-for-callers"></a>呼叫者的注意事項
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)會傳回此介面。

## <a name="methods-in-vtable-order"></a>以 Vtable 順序的方法
 這個介面會實作為下列方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|從列舉中抓取下一組[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|略過指定數目的專案。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|將列舉重設為第一個專案。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|抓取目前列舉的複本。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|抓取列舉中的專案數。|

## <a name="remarks"></a>備註
 這個介面可讓 debug engine 列舉陣列中的一組物件。

## <a name="requirements"></a>需求
 標頭： ee。h

 命名空間： VisualStudio。 Interop

 元件： VisualStudio. Interop .dll

## <a name="see-also"></a>請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)