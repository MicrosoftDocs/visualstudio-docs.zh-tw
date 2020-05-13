---
title: COMPUTER_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27794dff51646b72dbbfda81ead02e5206ade78b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737663"
---
# <a name="computer_info"></a>COMPUTER_INFO
描述運行調試器的電腦。

## <a name="syntax"></a>語法

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>成員
`wProcessorArchitecture`\
標識微處理器的體系結構。

`wSuiteMask`\
標識套件掩碼。

`dwOperatingSystemVersion`\
操作系統版本號。

## <a name="remarks"></a>備註
此結構由[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)方法返回。

## <a name="requirements"></a>需求
標題: Msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [取得電腦資訊](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
