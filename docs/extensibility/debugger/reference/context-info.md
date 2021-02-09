---
title: CONTEXT_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a95808383d4d75810f17b4da121a11025b6f894
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912992"
---
# <a name="context_info"></a>CONTEXT_INFO
此結構描述記憶體內容或程式碼內容。

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
[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)列舉的旗標組合，可指定要填寫的欄位<strong>。</strong>

`bstrModuleUrl`\
內容所在的模組名稱。

`bstrFunction`\
內容所在的函式名稱。

`posFunctionOffset`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構，識別與程式碼內容相關聯之函式的行和資料行位移。

`bstrAddress`\
程式碼中指定內容所在的位址。

`bstrAddressOffset`\
程式碼中指定內容所在位置的位址位移。

`bstrAddressAbsolute`\
記憶體中指定內容所在的絕對位址。

## <a name="remarks"></a>備註
從呼叫 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 方法時，會傳回這個結構。

此結構的一般用途是支援 **記憶體** 偵錯工具視窗。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
