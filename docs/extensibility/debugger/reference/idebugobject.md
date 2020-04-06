---
title: IDebugObject |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726308"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示活頁夾為封裝符號和表達式的值而創建的物件。

## <a name="syntax"></a>語法

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面以表示物件。

## <a name="notes-for-callers"></a>通話備註
 此介面是表達式賦值器在解析表達式中使用的所有物件的基類。 它通過調用[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法返回。 [查詢介面](/cpp/atl/queryinterface)從此介面獲取更專業的介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugObject`。

|方法|描述|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|獲取物件的大小。|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|獲取物件的值作為連續位元組系列。|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|設置連續位元組序列中物件的值。|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|設定此物件的引用值。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|獲取表示物件值位址的記憶體上下文。|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|在除錯引擎的位址空間中創建託管物件的副本。|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|測試此物件是否為空引用。|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|將物件與此對象進行比較。|
|[只閱讀](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|確定此物件是否為唯讀物件。|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|確定物件是否為透明代理。|

## <a name="remarks"></a>備註
 表達式賦值器使用此介面作為基類來表示解析樹中的物件。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
