---
title: IProperty 代理邊:原位更新物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714898"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
使用給定的數據物件更新物件的數據,並返回表示對象新數據的新數據物件。

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
[在]包含新[數據的 IEEData 儲存](../../../extensibility/debugger/reference/ieedatastorage.md)物件。

`dataOut`\
[出]返回包含替換`IEEDataStorage`數據的新物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法實際上更新物件的數據。 返回的[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件中的數據不需要與`IEEDataStorage`傳入 對象中的數據相同,但返回的物件必須反映屬性的當前值。

 傳入數據物件通常不由 EE 實現。 但是,此方法返回的對象始終由 EE 實現,它允許 EE 在`IEEDataStorage`所需的任何類上 實現介面。

 [Create替換物件](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)方法基於傳入數據物件創建數據物件,但不會影響屬性的原始數據。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
