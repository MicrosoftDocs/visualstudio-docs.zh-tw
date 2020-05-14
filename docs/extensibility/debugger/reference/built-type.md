---
title: BUILT_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 885f17b0841a39672c87be5bc7c947b2e0d9c7e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737692"
---
# <a name="built_type"></a>BUILT_TYPE
此結構指定有關從元數據獲取的欄位類型的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagTYPE_BUILT {
    ULONG32      ulAppDomainID;
    GUID         guidModule;
    IDebugField* pUnderlyingField;
} BUILT_TYPE;
```

```csharp
public struct BUILT_TYPE {
    public uint        ulAppDomainID;
    public Guid        guidModule;
    public IDebugField pUnderlyingField;
};
```

## <a name="members"></a>成員
`ulAppDomainID`\
符號來自的應用程式的 ID。 這用於唯一標識應用程式的實例。

`guidModule`\
包含此欄位的模組的 GUID。

`pUnderlyingField`\
標識與此生成欄位關聯的基礎欄位的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

## <a name="remarks"></a>備註
當`TYPE_INFO``TYPE_KIND_BUILT`結構欄位設定為[(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)枚[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)舉中的值`dwKind`)時, 此結構在TYPE_INFO結構中顯示為聯合的一部分。

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
