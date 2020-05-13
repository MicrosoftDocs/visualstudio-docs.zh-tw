---
title: IDebug運算式評估器2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7041456bf0f3ae7930a73399d43dbf7cac6b3b32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729150"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示表達式賦值器 (EE) 的增強版本。

## <a name="syntax"></a>語法

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由表達式賦值器實現。

## <a name="methods"></a>方法
 除了[IDebugExpression 評估器](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[取得服務](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|檢索給定其唯一標識符的服務物件。|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|預載入指定符號提供程式指定的模組。|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|使運算式賦值器 (EE) 指定除錯器引擎 (DE) 將用於讀取指標設定的回調介面。|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|設置除錯器中載入的通用語言執行時 (CLR) 的路徑。|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|使調試引擎能夠在初始化期間將回調傳遞給表達式賦值器。|
|[終止](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|停止並清理表達式賦值器。|

## <a name="requirements"></a>需求
 標題: Ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
