---
title: IDebugBinder3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735678"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面提供對類型、別名和自定義可視化工具服務的訪問。

## <a name="syntax"></a>語法

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎實現此介面以支援別名、自定義可視化器服務和對物件類型資訊的訪問。

## <a name="notes-for-callers"></a>通話備註
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面使用[查詢介面](/cpp/atl/queryinterface)獲取此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 除了[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面提供的方法外,此介面還實現了以下功能:

|方法|描述|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|檢索表示此物件綁定到的記憶體的記憶體物件。|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|檢索與此對象關聯的異常(如果有),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|檢索給定其名稱的別名,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|檢索此物件的所有別名的陣列,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|獲取與此對象關聯的參數類型數,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|檢索與此物件關聯的參數類型的清單,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|獲取可視化工具服務的介面,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|將物件位置或 64 位元記憶體位址轉換為記憶體上下文。|

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
