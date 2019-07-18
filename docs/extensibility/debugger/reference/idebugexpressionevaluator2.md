---
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b00085cdeb743bda991805cd0fb6d44302560f2d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343857"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示的運算式評估工具 (EE) 的增強型的版本。

## <a name="syntax"></a>語法

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具會實作這個介面。

## <a name="methods"></a>方法
 上的方法除了[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|擷取服務物件指定的唯一識別碼。|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|預先載入指定的符號提供者所指定的模組。|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|可讓運算式評估工具 (EE)，指定偵錯工具引擎 (DE) 將用來讀取計量設定的回呼介面。|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|設定 common language runtime (CLR) 載入偵錯工具的路徑。|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|可讓要傳遞給運算式評估工具的回呼，在初始化期間的偵錯引擎。|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|停止和清除運算式評估工具。|

## <a name="requirements"></a>需求
 標頭：Ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll