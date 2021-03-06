---
description: 初始化這個物件的來源資料，並傳回包含初始資料的物件。
title: IPropertyProxyEESide：： InitSourceDataProvider |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd1040c6269b9d394e6f0968f595c71cf1576135
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224118"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
初始化這個物件的來源資料，並傳回包含初始資料的物件。

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

## <a name="parameters"></a>參數
`dataOut`\
擴展傳回 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 物件

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會執行初始化物件時所需的任何動作，讓它可以傳回物件資料上的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 介面。 這可讓您查看物件的資料，並在允許的情況下，由型別視覺化程式變更。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
