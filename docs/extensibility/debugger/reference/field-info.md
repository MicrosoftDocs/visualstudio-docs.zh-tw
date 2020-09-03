---
title: FIELD_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e2089746adecc583d04176afca18ad19826ea53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736891"
---
# <a name="field_info"></a>FIELD_INFO
此結構描述本機變數、參數或其他欄位。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>成員
`dwFields`\
[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)列舉中的旗標組合，可指定要填入哪些成員。

`bstrFullName`\
欄位的完整名稱。

`bstrName`\
欄位的簡短名稱。

`bstrType`\
欄位的型別。

`dwModifiers`\
描述欄位之 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 列舉中的旗標組合。

## <a name="remarks"></a>備註
此結構會傳遞至其填入的 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法。

## <a name="requirements"></a>需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
