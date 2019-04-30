---
title: IPropertyProxyEESide::GetInitialData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetInitialData
helpviewer_keywords:
- IPropertyProxyEESide::GetInitialData
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8fdfd41b8ab15a1c1b6e7b494d02c3e488c54c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865819"
---
# <a name="ipropertyproxyeesidegetinitialdata"></a>IPropertyProxyEESide::GetInitialData
傳回此物件的初始資料。

## <a name="syntax"></a>語法

```cpp
HRESULT GetInitialData(
   IEEDataStorage** dataOut
);
```

```csharp
int GetInitialData(
   out IEEDataStorage dataOut
);
```

#### <a name="parameters"></a>參數
 `dataOut`

 [out]傳回[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)物件，其中包含這個物件的初始資料。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)