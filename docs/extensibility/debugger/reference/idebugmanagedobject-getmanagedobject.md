---
title: IDebug託管物件:獲取託管物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7080760b174c51d62c44cd2757944948e0104ca
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727744"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
返回表示託管對象的介面。

## <a name="syntax"></a>語法

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>參數
`ppManagedObject`\
[出]返回表示託管對象的介面。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 可以查詢從此方法返回的介面,以便查詢託管類實現的任何介面,從而允許調用其方法。

## <a name="see-also"></a>另請參閱
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
