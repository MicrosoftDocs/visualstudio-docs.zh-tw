---
description: 抓取指定 proxy 識別碼的屬性 proxy 介面。
title: IPropertyProxyProvider：： GetPropertyProxy |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9212e9c7d0392bf9c4d6229ba76e40ea21f0686
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222584"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
抓取指定 proxy 識別碼的屬性 proxy 介面。

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
在所需屬性 proxy 的識別碼。

`proxy`\
擴展傳回 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 為了支援外部型別視覺化，這個方法通常會將呼叫轉送至 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) 方法。 如需如何取得 IEEVisualizerService 的詳細資訊，請參閱 [視覺化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
