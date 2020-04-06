---
title: IDebugarray物件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736233"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示託管陣列物件,並允許表達式賦值器 (EE) 確定陣列的基本索引(下限)。

## <a name="syntax"></a>語法

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>實施者說明
 這由託管調試引擎 (DE) 實現。

## <a name="methods"></a>方法
 除了[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|給定陣列中的維度數,檢索每個索引的基本索引(下限)。|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|確定陣列是否定義了基本索引(下限)。|

## <a name="remarks"></a>備註
 表達式賦值器使用此介面表示解析樹中的託管陣列。

## <a name="requirements"></a>需求
 標題: Ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
