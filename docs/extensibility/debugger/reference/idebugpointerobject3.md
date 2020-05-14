---
title: IDebugPointer物件3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725460"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示解析樹中的指標,並擴展**IDebugPointerObject**介面。

## <a name="syntax"></a>語法

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器 (EE) 實現此介面。

## <a name="methods"></a>方法
 除了[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|檢索指標的位址。|

## <a name="requirements"></a>需求
 標題: Ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
