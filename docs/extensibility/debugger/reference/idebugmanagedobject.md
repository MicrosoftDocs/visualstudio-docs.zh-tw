---
title: IDebugManagedObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90540aaf5f7e409c8fc7fa44126f195230317f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929806"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面可讓運算式評估工具 (EE) 在實值類別實例上呼叫屬性或方法 (例如 `System.Decimal`) ，以及設定其值，而不需在所要進行的程式上呼叫 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 。

## <a name="syntax"></a>Syntax

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行這個介面，以代表 managed 程式碼物件，例如變數。

## <a name="notes-for-callers"></a>呼叫者注意事項
 若要取得這個介面，請在代表實值類別實例的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)上呼叫[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)的方法之外，介面也會 `IDebugManagedObject` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|傳回代表 managed 程式碼物件的介面，以及可從中取得任何適當 managed 程式碼介面的介面。|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|將這個物件的值設定為指定之 managed 程式碼物件的值。|

## <a name="remarks"></a>備註
 運算式評估工具會使用這個介面將 managed 程式碼物件儲存在剖析樹狀結構中。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
