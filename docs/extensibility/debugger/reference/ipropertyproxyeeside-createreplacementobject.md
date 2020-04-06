---
title: IPropertyProxyEEside:創建替換物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715045"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
創建特定於運算式賦值器 (EE) 的資料物件的副本。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>參數
`dataIn`\
[在]保存要複製數據的[IEEData 儲存](../../../extensibility/debugger/reference/ieedatastorage.md)物件。

`dataOut`\
[出]返回新`IEEDataStorage`物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法被賦予一個[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件,表示位元組陣列。 此傳入數據物件通常不由 EE 實現。 但是,此方法返回的對象始終由 EE 實現,它允許 EE 在`IEEDataStorage`所需的任何類上 實現介面。

 請注意,傳入`IEEDataStorage`物件提供的數據必須是`IEEDataStorage`傳出 物件中相同的數據。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
