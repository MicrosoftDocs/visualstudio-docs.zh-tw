---
description: 針對 (EE) 的運算式評估工具建立特定資料物件的複本。
title: IPropertyProxyEESide：： CreateReplacementObject |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 341ca3d00a433c4bb36bc22ab2d598d7b454842a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225704"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
針對 (EE) 的運算式評估工具建立特定資料物件的複本。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>參數
`dataIn`\
在保存要複製之資料的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 物件。

`dataOut`\
擴展傳回新的 `IEEDataStorage` 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 系統會為這個方法提供代表位元組陣列的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 物件。 此內送資料物件通常不是由 EE 所執行。 不過，這個方法所傳回的物件一律會由 EE 執行，這可讓 EE `IEEDataStorage` 在需要的任何類別上執行介面。

 請注意，傳入物件所提供的資料 `IEEDataStorage` 必須是連出物件中的相同資料 `IEEDataStorage` 。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
