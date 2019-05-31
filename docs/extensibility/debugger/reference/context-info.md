---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c50d5ea930f05d22b68416978909cceca17727d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346457"
---
# <a name="contextinfo"></a>CONTEXT_INFO
此結構描述的記憶體內容或程式碼內容。

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
從他的旗標的組合[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)列舉，指定哪些欄位都已填寫<strong>。</strong>

`bstrModuleUrl`\
內容所在位置的模組名稱。

`bstrFunction`\
函式名稱，其內容所在的位置。

`posFunctionOffset`\
A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構，辨識與程式碼內容相關聯的函式的行和資料行位移。

`bstrAddress`\
指定之內容所在的程式碼中的位址。

`bstrAddressOffset`\
在指定的內容所在的程式碼中的位址位移。

`bstrAddressAbsolute`\
指定之內容所在的記憶體中的絕對位址。

## <a name="remarks"></a>備註
此結構會從呼叫傳回[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)方法。

此結構的典型用法是支援**記憶體**偵錯視窗。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
