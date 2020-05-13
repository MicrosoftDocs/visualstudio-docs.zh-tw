---
title: IEnum調試自定義屬性::下一個 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08228fe4a630eac37c38f4eb247dc91678d8e2e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717230"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
檢索枚舉序列中指定數量的自定義屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>參數
`celt`\
[在]要檢索的元素數。 還指定`rgelt`數位的最大大小。

`rgelt`\
[出]要填充的[IDebugCustom 屬性](../../../extensibility/debugger/reference/idebugcustomattribute.md)物件的陣列。

`pceltFetched`\
[出]返回中`rgelt`實際返回的元素數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE`返回的元素數少於請求的元素數,則返回;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
