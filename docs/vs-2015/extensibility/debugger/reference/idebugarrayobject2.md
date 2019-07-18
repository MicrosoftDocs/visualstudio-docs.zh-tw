---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d68b0db20150bd81a9b2b4aef29c78701a6bc8ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440693"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示 managed 的陣列物件，並可讓運算式評估工具 (EE) 來判斷陣列的基底的索引 （下限）。

## <a name="syntax"></a>語法

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>實作者的附註
 這被實作 managed 偵錯引擎 (DE)。

## <a name="methods"></a>方法
 上的方法除了[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|擷取陣列中指定的維度數目的每個索引的基底的索引 （下限）。|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|判斷陣列是否具有定義的基底索引 （下限）。|

## <a name="remarks"></a>備註
 運算式評估工具會使用此介面來代表剖析樹狀結構中的 managed 的陣列。

## <a name="requirements"></a>需求
 標頭：Ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll