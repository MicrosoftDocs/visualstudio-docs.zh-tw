---
title: IDebugObject2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726082"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面提供有關物件的其他資訊。

## <a name="syntax"></a>語法

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面,以支援別名和對物件資訊的訪問。

## <a name="notes-for-callers"></a>通話備註
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用[查詢介面](/cpp/atl/queryinterface)獲取此介面。 此外[,GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)傳回此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 除了[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面上的方法`IDebugObject2`外, 該介面還實現了以下功能:

|方法|描述|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|獲取可能支援此物件表示的屬性的欄位或變數(如果有)。|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|獲取表示此物件值的託管代碼物件。|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|為此物件創建唯一 ID 或返回現有別名。|
|[取得別名](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|獲取與此物件關聯的別名(如果有)。|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|獲取此對象的類型。|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|確定此物件是否表示用戶數據。|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|確定"編輯"和"繼續"狀態是否不再有效。<br /><br /> 自定義表達式賦值器不實現此方法(應始終返回`E_NOTIMPL`)。|

## <a name="remarks"></a>備註
 有關別名的討論,請參閱[IDebugAlias。](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [取得物件](../../../extensibility/debugger/reference/idebugalias-getobject.md)
