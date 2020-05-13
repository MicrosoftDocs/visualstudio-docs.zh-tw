---
title: IDebug託管物件::從託管對象設置 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727707"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
從作為參數提供的值類的實例中設置值類物件的實例的值。

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
[在]表示包含新值的託管物件的介面。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法用於更改[IDebug 託管物件](../../../extensibility/debugger/reference/idebugmanagedobject.md)表示的託管物件。

## <a name="see-also"></a>另請參閱
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
