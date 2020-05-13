---
title: IDebug託管物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727687"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面使表達式賦值器 (EE) 能夠調用值類實例的屬性或方法`System.Decimal`(例如 ),並在不調用正在調試的程式上的[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)的情況下設置其值。

## <a name="syntax"></a>語法

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面以表示託管代碼物件(如變數)。

## <a name="notes-for-callers"></a>通話備註
 要取得此介面,請呼叫表示值類別的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)上的[Get託管除錯物件](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)繼承的方法`IDebugManagedObject`外, 介面還公開了以下方法。

|方法|描述|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|返回表示託管代碼物件的介面,並從中獲取任何適當的託管代碼介面。|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|將此物件的值設置為指定的託管代碼物件的值。|

## <a name="remarks"></a>備註
 表達式賦值器使用此介面將託管代碼物件存儲在解析樹中。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [評價](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
