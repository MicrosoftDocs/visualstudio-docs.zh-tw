---
description: 此結構會指定取自中繼資料之欄位類型的相關資訊。
title: METADATA_TYPE |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8f0c8341213dfbe15dcf9a6f5a5fc421c0ebab3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225483"
---
# <a name="metadata_type"></a>METADATA_TYPE
此結構會指定取自中繼資料之欄位類型的相關資訊。

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
 符號的來源應用程式識別碼。 這是用來唯一識別應用程式的實例。

 `guidModule`\
 包含此欄位之模組的 GUID。

 `tokClass`\
 此類型的中繼資料標記識別項。

 [C + +] `_mdToken` 是 `typedef` 32 位的 `int` 。

## <a name="remarks"></a>備註
 當結構的[](../../../extensibility/debugger/reference/type-info.md) `dwKind` 欄位 `TYPE_INFO` 設定為 `TYPE_KIND_METADATA` ([dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉) 中的值時，這個結構會顯示為 TYPE_INFO 結構中聯集的一部分。

 `tokClass`值是可唯一識別類型的元資料標記。 如需有關如何解讀中繼資料 token 識別碼之最高位的詳細資訊，請參閱 `CorTokenType` .Net FRAMEWORK SDK 中 corhdr.h 檔案的列舉。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
