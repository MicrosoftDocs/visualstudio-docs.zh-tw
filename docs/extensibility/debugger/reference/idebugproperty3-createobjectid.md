---
title: IDebug屬性3::創建物件ID |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721169"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
為此屬性創建唯一 ID,以確保它在所有其他屬性中是唯一的。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當會話調試管理器希望確保此屬性在所有其他屬性之間唯一標識時,將調用此方法。 除錯引擎 (DE) 支援此方法,除非它處理的屬性已被唯一標識。 如果 DE 不支援此方法,會`E_NOTIMPL`傳回 。

 調用[銷毀ObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)方法`CreateObjectID`時,將銷毀使用的任何唯一 ID;這也標誌著唯一標識此屬性的需要的結束。

> [!NOTE]
> 沒有檢索此唯一 ID 的方法,因此當`CreateObjectID`調用 該方法時,DE 可以執行所需的任何唯一 ID 操作。

## <a name="see-also"></a>另請參閱
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
