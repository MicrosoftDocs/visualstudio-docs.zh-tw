---
description: 指定反組解碼資料流程的範圍。
title: DISASSEMBLY_STREAM_SCOPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 828d6b9afc659a09a4f1091c741e6246512de025
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096170"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
指定反組解碼資料流程的範圍。

## <a name="syntax"></a>Syntax

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
指定反組譯程式碼內容會產生比用戶端通常想要在單一呼叫中取得更多的輸出。

`DSS_FUNCTION`\
指定應拆解程式碼內容所包含的函式。 指定當 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 方法傳回時，反組解碼資料流程表示函式。

`DSS_MODULE`\
當方法傳回時 `IDebugDisassemblyStream2::GetScope` ，會指定反組解碼資料流程代表模組。

`DSS_ALL`\
指定整個位址空間的反組譯。

## <a name="remarks"></a>備註
傳遞為 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 方法的引數，並由 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) 方法傳回。

這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
