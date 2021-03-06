---
description: 表示剖析樹狀結構中的指標，並擴充 IDebugPointerObject 介面。
title: IDebugPointerObject3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3be0c3b96e5f9d8edb82acc2f60eefe709943243
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087518"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示剖析樹狀結構中的指標，並擴充 **IDebugPointerObject** 介面。

## <a name="syntax"></a>Syntax

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具 (EE) 會執行這個介面。

## <a name="methods"></a>方法
 除了 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|捕獲指標的位址。|

## <a name="requirements"></a>規格需求
 標頭： Ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
