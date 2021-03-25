---
description: 表示 (EE) 的增強版運算式評估工具。
title: IDebugExpressionEvaluator2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3689f667508f6453f0e4cd4181d14f42ca7b7541
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077300"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示 (EE) 的增強版運算式評估工具。

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由運算式評估工具所執行。

## <a name="methods"></a>方法
 除了 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|取得服務物件的唯一識別碼。|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|預先載入指定的符號提供者所指定的模組。|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|讓運算式評估工具 (EE) 指定偵錯工具引擎 (DE) 將用來讀取度量設定的回呼介面。|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|設定在偵錯工具中載入之 common language runtime (CLR) 的路徑。|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|讓 debug engine 在初始化期間將回呼傳遞給運算式評估工具。|
|[終止](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|停止並清除運算式評估工具。|

## <a name="requirements"></a>規格需求
 標頭： Ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
