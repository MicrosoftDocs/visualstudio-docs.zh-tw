---
title: IEE可視化服務提供者::創建可視化服務 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717915"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
此方法創建視覺化工具服務。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>參數
`binder`\
[在][IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件傳遞給[評估同步](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。

`pSymProv`\
[在]傳遞給的[IDebugSymbol](../../../extensibility/debugger/reference/idebugsymbolprovider.md)`IDebugParsedExpression::EvaluateSync`提供程式物件。

`pAddress`\
[在]傳遞給[的 IDebug](../../../extensibility/debugger/reference/idebugaddress.md)`IDebugParsedExression::EvaluateSync`位址物件。

`dataProvider`\
[在]實現[IEEVisualizerData Provider 介面](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)的物件(由運算式賦值器提供)。

`ppService`\
[出]創建的服務。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 `binder``pSymProv`與`pAddress`參數都傳遞給`IDebugParsedExpression::EvaluateSync`方法 。 `CreateVisualizerService`僅從`IDebugParsedExpression::EvaluateSync`表達式評估器對類型可視化器的支援調用。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
