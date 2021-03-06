---
description: 描述正在執行偵錯工具的電腦。
title: COMPUTER_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7ebcee7270eb187998ce7c6078277dd90897012
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096455"
---
# <a name="computer_info"></a>COMPUTER_INFO
描述正在執行偵錯工具的電腦。

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
識別微處理器的架構。

`wSuiteMask`\
識別套件遮罩。

`dwOperatingSystemVersion`\
作業系統版本號碼。

## <a name="remarks"></a>備註
[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)方法會傳回這個結構。

## <a name="requirements"></a>規格需求
標頭： Msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
