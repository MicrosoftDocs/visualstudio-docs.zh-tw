---
description: 從提供作為參數的實值類別的實例，設定實值類別物件的實例值。
title: IDebugManagedObject：： SetFromManagedObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c00e61de35e0cc9c33845236d8103bcd16cebfa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076845"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
從提供作為參數的實值類別的實例，設定實值類別物件的實例值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>參數
`pManagedObject`\
在介面，表示包含新值的 managed 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法是用來變更 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) 物件所代表的 managed 物件。

## <a name="see-also"></a>另請參閱
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
