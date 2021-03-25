---
description: 此介面提供類型、別名和自訂視覺化服務的存取權。
title: IDebugBinder3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29d8b642a66a75dd561b0a87cd5fa083e841139c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085152"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面提供類型、別名和自訂視覺化服務的存取權。

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine 會執行這個介面，以支援別名、自訂的視覺化檢視服務，以及物件類型資訊的存取。

## <a name="notes-for-callers"></a>呼叫者注意事項
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面會使用[QueryInterface](/cpp/atl/queryinterface)取得這個介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 除了 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 介面所提供的方法之外，此介面還會執行下列動作：

|方法|描述|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|抓取代表這個物件所系結之記憶體的記憶體物件。|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|如果有任何) ，則抓取與這個物件相關聯的例外狀況 (|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|抓取別名的指定名稱，|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|抓取此物件之所有別名的陣列。|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|取得與此物件相關聯的引數類型數目。|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|抓取與這個物件相關聯的引數類型清單。|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|取得視覺化程式服務的介面。|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|將物件位置或64位的記憶體位址轉換成記憶體內容。|

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
