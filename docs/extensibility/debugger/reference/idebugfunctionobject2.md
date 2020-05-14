---
title: IDebug函數物件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4150480d2e6686992d78727b6fed817da270145
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728424"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示函數並增強[IDebug 函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。

## <a name="syntax"></a>語法

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器 (EE) 實現此介面以表示函數。

## <a name="notes-for-callers"></a>通話備註
 此介面的方法以下列方式遞延**IDebug 函式物件**的方法:

- **IDebug評估**方法採用標誌。

- **CreateObject**方法採用標誌和超時。

- **使用長度創建 StringObject**方法需要一段長度。

## <a name="methods"></a>方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|創建使用建構函數給定評估標誌設置和超時值的物件。|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|建立具有指定長度的字串物件。|
|[評價](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|調用函數並將結果值作為物件返回。|

## <a name="requirements"></a>需求
 標題: Ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
