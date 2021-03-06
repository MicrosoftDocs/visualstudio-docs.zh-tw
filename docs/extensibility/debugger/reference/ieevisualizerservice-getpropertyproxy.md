---
description: 這個方法會傳回屬性物件的 proxy。
title: IEEVisualizerService：： GetPropertyProxy |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetPropertyProxy
helpviewer_keywords:
- IEEVisualizerService::GetPropertyProxy method
ms.assetid: 748750f4-76e7-4580-9da2-afba07681b37
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbcaa460546443dcbc714a3fa72a6ebc7479dfc3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222857"
---
# <a name="ieevisualizerservicegetpropertyproxy"></a>IEEVisualizerService::GetPropertyProxy
這個方法會傳回屬性物件的 proxy。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPropertyProxy(
   DWORD                  dwID,
   IPropertyProxyEESide** proxy
);
```

```csharp
int GetPropertyProxy(
   uint                     dwID,
   out IPropertyProxyEESide proxy
);
```

## <a name="parameters"></a>參數
`dwID`\
在要取得之屬性 proxy 的識別碼。

`proxy`\
擴展在 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 介面中實作為所需的 proxy。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
- [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 會將要求傳遞給這個方法，作為其對視覺化類型的支援。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)
