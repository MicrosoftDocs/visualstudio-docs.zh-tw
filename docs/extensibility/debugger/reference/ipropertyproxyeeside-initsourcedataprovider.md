---
title: IPropertyProxyEESide::InitSourceDataProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb0d2b960c2bafd1a2d502e41c8a435a5205d11
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687480"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
初始化此物件的來源資料，並傳回物件，其中包含初始資料。

## <a name="syntax"></a>語法

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

#### <a name="parameters"></a>參數
 `dataOut`

 [out]傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會執行任何必要初始化物件，因此它會傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)介面上物件的資料。 這可讓物件的資料檢視而且，如果允許，請變更類型視覺化檢視。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)