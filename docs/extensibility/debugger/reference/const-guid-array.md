---
title: CONST_GUID_ARRAY |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONST_GUID_ARRAY
helpviewer_keywords:
- CONST_GUID_ARRAY structure
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0021ef24e0cafec0119263d2c74175f0d38d784
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737630"
---
# <a name="const_guid_array"></a>CONST_GUID_ARRAY
儲存 s 清單`GUID`的結構 。

## <a name="syntax"></a>語法

```cpp
typedef struct tagCONST_GUID_ARRAY {
    DWORD       dwCount;
    CONST GUID* Members;
} CONST_GUID_ARRAY;
```

```csharp
public struct CONST_GUID_ARRAY {
    public uint   dwCount;
    public Guid[] Members;
}
```

## <a name="members"></a>成員
`dwCount`\
陣列中的`GUID``Members`s 數。

`Members`\
s`GUID`陣組。

## <a name="remarks"></a>備註
此結構傳遞給[發佈程式](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)方法,並從[獲取提供程式處理數據和](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) [WatchForProvider 事件](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)方法返回。

此結構實例的所有者負責釋放分配的任何記憶體。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
