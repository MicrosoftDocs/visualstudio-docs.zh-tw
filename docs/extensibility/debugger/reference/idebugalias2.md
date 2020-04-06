---
title: IDebugAlias2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00e13da257c5477b3834ebb85bf6d481fe699362
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736362"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 表示變數的數位別名,並使表達式賦值器 (EE) 能夠獲取別名的應用程式域。

## <a name="syntax"></a>語法

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由託管調試引擎 (DE) 實現。

## <a name="methods"></a>方法
 除了[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|檢索應用程式域的標識碼。|

## <a name="remarks"></a>備註
 別名是字串形式的十進位數字,後跟 # 字元,例如 1001*。

## <a name="requirements"></a>需求
 標題: Ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
