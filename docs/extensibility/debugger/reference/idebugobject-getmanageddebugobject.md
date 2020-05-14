---
title: IDebugObject:獲取託管調試物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726685"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
在除錯引擎的位址空間中創建託管物件的副本。

## <a name="syntax"></a>語法

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>參數
`ppObject`\
[出]傳回表示新的建立的託管物件的[IDebug 託管物件](../../../extensibility/debugger/reference/idebugmanagedobject.md)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。 如果此[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)不表示託管值類實例,則返回E_FAIL。

## <a name="remarks"></a>備註
 此[IDebugObject 對象](../../../extensibility/debugger/reference/idebugobject.md)必須表示託管值類實`System.Decimal`例,如實例。 通過具有本地副本,可以消除調用[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)的開銷。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
