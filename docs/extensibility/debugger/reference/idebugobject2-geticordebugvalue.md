---
title: IDebugObject2::獲取ICorDebug值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d52701b916650bc142038ffd96dcab8b05ec6da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726124"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
獲取表示與此物件關聯的值的託管代碼物件。

## <a name="syntax"></a>語法

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>參數
`ppUnk`\
[出]`IUnknown`表示此別名的介面。 可以查詢介面的此`ICorDebugValue`介面。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 該`ICorDebugValue`對像是表示值的通用語言運行時介面。

## <a name="see-also"></a>另請參閱
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
