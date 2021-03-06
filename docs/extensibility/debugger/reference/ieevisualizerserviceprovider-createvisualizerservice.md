---
description: 這個方法會建立視覺化服務。
title: IEEVisualizerServiceProvider：： CreateVisualizerService |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b304dd8fe2845cf6c1201e6e128f8b89ec47b1b6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222818"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
這個方法會建立視覺化服務。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>參數
`binder`\
在傳遞至[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)的[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。

`pSymProv`\
在傳遞至的 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 物件 `IDebugParsedExpression::EvaluateSync` 。

`pAddress`\
在傳遞至的 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件 `IDebugParsedExression::EvaluateSync` 。

`dataProvider`\
在 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 介面的物件， (運算式評估工具所提供) 。

`ppService`\
擴展已建立的服務。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 `binder`、 `pSymProv` 和 `pAddress` 參數全都傳遞給 `IDebugParsedExpression::EvaluateSync` 方法。 `CreateVisualizerService` 只有在 `IDebugParsedExpression::EvaluateSync` 運算式評估工具支援型別視覺化時，才會呼叫。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
