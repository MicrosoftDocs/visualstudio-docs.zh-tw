---
title: IDebugObject2::用戶數據 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce4a7035ac3786f0cc1644e2ebbb0c142167e2b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726085"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
確定物件是否表示用戶數據。

## <a name="syntax"></a>語法

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>參數
`pfUser`\
[出]如果物件表示用戶`TRUE`數據,則返回非零 (),零`FALSE`( ) () 如果沒有。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 用戶數據是被指定為 JustMyCode 的模組的一部分的任何物件(一個使用者可配置的選項,將模組標記為用戶代碼,因此在堆疊追蹤中可見)。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
