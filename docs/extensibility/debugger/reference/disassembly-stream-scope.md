---
title: DISASSEMBLY_STREAM_SCOPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737267"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
指定拆解流的範圍。

## <a name="syntax"></a>語法

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>欄位
`DSS_HUGE`\
指定拆解代碼上下文產生的輸出將超過用戶端在單個調用中通常希望檢索的輸出數。

`DSS_FUNCTION`\
指定應拆解代碼上下文中包含的函數。 指定拆解流表示函數,當由[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)方法返回時。

`DSS_MODULE`\
當由`IDebugDisassemblyStream2::GetScope`方法返回時,指定拆解流表示模組。

`DSS_ALL`\
指定整個位址空間的拆解。

## <a name="remarks"></a>備註
作為參數傳遞給[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法,並由[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)方法返回。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
