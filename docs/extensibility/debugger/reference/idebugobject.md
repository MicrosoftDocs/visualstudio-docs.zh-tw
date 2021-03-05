---
description: 這個介面代表系結器建立的物件，用來封裝符號和運算式的值。
title: IDebugObject |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14c405c9dbe3d1cbfdf61c606b995a686e063661
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170189"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面代表系結器建立的物件，用來封裝符號和運算式的值。

## <a name="syntax"></a>Syntax

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行此介面來代表物件。

## <a name="notes-for-callers"></a>呼叫者注意事項
 此介面是運算式評估工具在剖析的運算式中使用之所有物件的基類。 它是由 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) 方法的呼叫所傳回。 [QueryInterface](/cpp/atl/queryinterface) 從這個介面取得更特製化的介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugObject` 。

|方法|描述|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|取得物件的大小。|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|以連續的位元組序列取得物件的值。|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|從連續的位元組序列設定物件的值。|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|設定這個物件的參考值。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|取得表示物件值之位址的記憶體內容。|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|在 debug 引擎的位址空間中建立 managed 物件的複本。|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|測試這個物件是否為 null 參考。|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|比較物件與此物件。|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|判斷此物件是否為唯讀。|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|判斷物件是否為透明的 proxy。|

## <a name="remarks"></a>備註
 運算式評估工具會使用這個介面作為基類，以表示剖析樹狀結構中的物件。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
