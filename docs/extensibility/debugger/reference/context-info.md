---
title: CONTEXT_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737563"
---
# <a name="context_info"></a>CONTEXT_INFO
此結構描述記憶體上下文或代碼上下文。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>成員
`dwFields`\
[他CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)的旗標中的旗標的組合,用於指定填寫哪些欄位<strong>。</strong>

`bstrModuleUrl`\
上下文所在的模組的名稱。

`bstrFunction`\
上下文所在的函數名稱。

`posFunctionOffset`\
標識與代碼上下文關聯的函數的行和列偏移的[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。

`bstrAddress`\
給定上下文所在的代碼中的位址。

`bstrAddressOffset`\
給定上下文所在的代碼中位址的偏移量。

`bstrAddressAbsolute`\
給定上下文所在的記憶體中的絕對位址。

## <a name="remarks"></a>備註
此結構從對[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)方法的調用返回。

此結構的典型用途是支援**記憶體**調試視窗。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
