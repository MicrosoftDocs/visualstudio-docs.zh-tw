---
description: 此結構代表方法或函數的傳回值。
title: METADATA_ADDRESS_RETVAL |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e28e0c32d5039ba0deda9a8c6801e6969c4ad96
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079877"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
此結構代表方法或函數的傳回值。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>成員
 `tokMethod`\
 這個傳回值適用之方法的識別碼。

 `dwCorType`\
 傳回值的基底類型。 這是 `CorElementType` .NET FRAMEWORK SDK corhdr.h .h 檔案中定義之列舉的值。

 `dwSigSize`\
 傳回值簽章的大小 (儲存在) 中 `rgSig` 。

 `rgSig`\
 形成傳回值簽章的位元組陣列。

## <a name="remarks"></a>備註
 當結構的[](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 欄位 `DEBUG_ADDRESS_UNION` 設定為 `ADDRESS_KIND_RETVAL` ([ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉) 中的值時，此結構就是 DEBUG_ADDRESS_UNION 結構中聯集的一部分。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
