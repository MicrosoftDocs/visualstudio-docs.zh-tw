---
title: IDebugAlias |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736523"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示變數的數字別名。 別名只是變數的不同名稱。

## <a name="syntax"></a>語法

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器 (EE) 實現此介面以支援變數的數位別名。

## <a name="notes-for-callers"></a>通話備註
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)為特定對象創建別名。 要搜尋別名,請使用[「尋找別名](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)」或[「獲取所有別名](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)」 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 以下方法在介面中`IDebugAlias`定義。

|方法|描述|
|------------|-----------------|
|[取得物件](../../../extensibility/debugger/reference/idebugalias-getobject.md)|獲取此別名引用的物件。|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|獲取別名名稱。|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|檢索提供`ICorDebugValue`對此物件(僅限託管代碼)的託管代碼信息的訪問的介面。|
|[處置](../../../extensibility/debugger/reference/idebugalias-dispose.md)|將此別名標記為不再使用。|

## <a name="remarks"></a>備註
 別名是字串形式的十進位數字,後跟 # 字元,例如 1001*。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
