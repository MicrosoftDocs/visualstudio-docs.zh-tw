---
title: IDebugProperty3::D對象ID |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721189"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
銷毀與此屬性關聯的唯一 ID,指示調用方不再關心從所有其他屬性唯一標識此屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果調試引擎不需要支援屬性的唯一 ID(因為它已在內部唯一地跟蹤它們),則只需`E_NOTIMPL`返回 此方法即可。

 當調用方希望確保此屬性在所有其他屬性中唯一標識時,使用調用[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)方法創建唯一 ID。

## <a name="see-also"></a>另請參閱
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
