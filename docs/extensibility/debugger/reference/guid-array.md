---
description: 描述可用的偵錯工具引擎之唯一識別碼陣列。
title: GUID_ARRAY |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbdc8465bef0795649fef5b169a221a3e7b7178c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162416"
---
# <a name="guid_array"></a>GUID_ARRAY
描述可用的偵錯工具引擎之唯一識別碼陣列。

## <a name="syntax"></a>語法

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>成員
`dwCount`\
陣列中的唯一識別碼數目。

`Members`\
包含唯一識別碼的陣列。

## <a name="remarks"></a>備註
[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)方法會傳回這個結構。

## <a name="requirements"></a>規格需求
標頭： Msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
