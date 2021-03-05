---
description: 代表變數的數值別名。
title: IDebugAlias |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fd5639c510ba5a4a346c7a6f2630e7f14ddf036
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143879"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 代表變數的數值別名。 別名只是變數的不同名稱。

## <a name="syntax"></a>Syntax

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具 (EE) 會執行這個介面，以支援變數的數值別名。

## <a name="notes-for-callers"></a>呼叫者注意事項
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 會建立特定物件的別名。 若要搜尋別名，請使用 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) 或 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 以下是在介面中定義的方法 `IDebugAlias` 。

|方法|描述|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|取得此別名所參考的物件。|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|取得別名名稱。|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|抓取 `ICorDebugValue` 介面，此介面可讓您僅)  (managed 程式碼，存取此物件的 managed 程式碼資訊。|
|[處置](../../../extensibility/debugger/reference/idebugalias-dispose.md)|將此別名標示為不再使用。|

## <a name="remarks"></a>備註
 別名是字串格式的十進位數，後面接著 # 字元，例如 1001 #。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
