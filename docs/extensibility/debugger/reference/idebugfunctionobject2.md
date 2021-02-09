---
title: IDebugFunctionObject2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 304269ba2a4f556cfe931157c445d7b4fc86f489
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929936"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 代表函式並增強 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面。

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具 (EE) 實作為函式的介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面的方法會以下列方式延遲這些 **IDebugFunctionObject** ：

- **IDebugEvaluate** 方法會接受旗標。

- **CreateObject** 方法會接受旗標和超時。

- **CreateStringObjectWithLength** 方法會採用長度。

## <a name="methods"></a>方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|建立物件，該物件會使用指定的評估旗標設定和超時值的函式。|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|建立具有指定長度的字串物件。|
|[評估](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|呼叫函數，並傳回產生的值做為物件。|

## <a name="requirements"></a>規格需求
 標頭： Ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
