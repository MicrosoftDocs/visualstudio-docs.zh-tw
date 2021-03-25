---
description: 代表 managed 陣列物件，並允許運算式評估工具 (EE) 判斷陣列 (下限) 的基底索引。
title: IDebugArrayObject2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 169f4df61bcd4a58e74e0d83cee362b3926d2b36
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067565"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 代表 managed 陣列物件，並允許運算式評估工具 (EE) 判斷陣列 (下限) 的基底索引。

## <a name="syntax"></a>Syntax

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這是由 managed debug engine (DE) 所執行。

## <a name="methods"></a>方法
 除了 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|針對指定陣列中的維度數目的每個索引，抓取基底索引 (下限) 。|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|判斷陣列是否有定義 (下限) 的基底索引。|

## <a name="remarks"></a>備註
 運算式評估工具會使用此介面來表示剖析樹狀結構中的 managed 陣列。

## <a name="requirements"></a>規格需求
 標頭： Ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
