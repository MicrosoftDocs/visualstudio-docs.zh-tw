---
title: IDebugAlias2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 171e9da3b25aa33ad3921f4ec5f841429490be72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944611"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 代表變數的數值別名，並讓運算式評估工具 (EE) 取得別名的應用程式域。

## <a name="syntax"></a>Syntax

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面是由 managed debug engine (DE) 所執行。

## <a name="methods"></a>方法
 除了 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|抓取應用程式域的識別碼。|

## <a name="remarks"></a>備註
 別名是字串格式的十進位數，後面接著 # 字元，例如 1001 #。

## <a name="requirements"></a>規格需求
 標頭： Ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
