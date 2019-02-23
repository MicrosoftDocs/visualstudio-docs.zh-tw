---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fbf93b3675e81c1774fc018b14c3c7f66641381
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723093"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示變數的數字的別名。 別名是只是不同的變數名稱。

## <a name="syntax"></a>語法

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具 (EE) 會實作這個介面來支援變數的數字的別名。

## <a name="notes-for-callers"></a>呼叫端資訊
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)建立特定物件的別名。 若要搜尋的別名，請使用[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)或是[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下列方法定義於`IDebugAlias`介面。

|方法|描述|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|取得這個別名所參考的物件。|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|取得別名名稱。|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|擷取`ICorDebugValue`介面，可提供存取權管理此物件 （僅限 managed 程式碼） 的程式碼資訊。|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|將此標示別名為不再使用。|

## <a name="remarks"></a>備註
 別名是十進位的數字，後面接著 # 字元，例如 1001 # 格式為字串。

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)