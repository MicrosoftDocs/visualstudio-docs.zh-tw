---
title: IPropertyProxyEESide：： InPlaceUpdateObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89f8185734c8c2ee15728328a510236bbbc50a21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895969"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
使用指定的資料物件來更新物件的資料，並傳回代表物件新資料的新資料物件。

## <a name="syntax"></a>語法

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>參數
`dataIn`\
在包含新資料的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 物件。

`dataOut`\
擴展傳回新 `IEEDataStorage` 的物件，其中包含已取代的資料。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會實際更新物件的資料。 傳回之 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 物件中的資料不需要與傳入物件中的資料相同 `IEEDataStorage` ，但是傳回的物件必須反映屬性的目前值。

 內送資料物件通常不是由 EE 所執行。 不過，這個方法所傳回的物件一律會由 EE 執行，這可讓 EE `IEEDataStorage` 在需要的任何類別上執行介面。

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)方法會根據傳入的資料物件建立資料物件，但不會影響屬性的原始資料。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
