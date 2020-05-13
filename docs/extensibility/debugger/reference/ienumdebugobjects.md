---
title: IEnum調試物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716260"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示實現[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面的物件的集合。

## <a name="syntax"></a>語法

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器實現此介面以提供實現[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面的物件集。 請注意,由於[存在GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)方法,這不是標準COM枚舉。

## <a name="notes-for-callers"></a>通話備註
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)傳回此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 此介面實現以下方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|從枚舉中取出的[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)。|
|[跳](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|跳過指定數量的條目。|
|[重設](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|將枚舉重置為第一個條目。|
|[複製](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|檢索當前枚舉的副本。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|檢索枚舉中的條目數。|

## <a name="remarks"></a>備註
 此介面允許調試引擎枚舉陣列中的一組物件。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
