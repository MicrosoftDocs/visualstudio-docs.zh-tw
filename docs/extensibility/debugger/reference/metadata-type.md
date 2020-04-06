---
title: METADATA_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714294"
---
# <a name="metadata_type"></a>METADATA_TYPE
此結構指定有關從元數據獲取的欄位類型的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>參數
 `ulAppDomainID`\
 符號來自的應用程式的 ID。 這用於唯一標識應用程式的實例。

 `guidModule`\
 包含此欄位的模組的 GUID。

 `tokClass`\
 此類型的元數據令牌 ID。

 [C++]`_mdToken`是`typedef`32`int`位元的 。

## <a name="remarks"></a>備註
 當`TYPE_INFO``TYPE_KIND_METADATA`結構欄位設定為[(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)枚[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)舉中的值`dwKind`)時, 此結構在TYPE_INFO結構中顯示為聯合的一部分。

 該`tokClass`值是唯一標識類型的元數據令牌。 有關如何解釋元數據令牌 ID 的上位的詳細資訊,請參閱`CorTokenType`.NET 框架 SDK 中的 corhdr.h 檔中的枚舉。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
