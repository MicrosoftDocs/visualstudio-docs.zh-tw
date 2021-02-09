---
title: DEBUG_ADDRESS_UNION |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76fc15389242de1011851492e3a68dc001534582
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899134"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
描述不同類型的位址。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>成員
`dwKind`\
[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉中的值，指定如何解讀聯集。

`addr.addrNative`\
[僅限 c + +]如果 = ADDRESS_KIND_NATIVE，則包含 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 結構 `dwKind` 。

`addr.addrThisRel`\
[僅限 c + +]如果 = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE，則包含[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 結構 `dwKind` 。

`addr.addUPhysical`\
[僅限 c + +]如果 = ADDRESS_KIND_UNMANAGED_PHYSICAL，則包含[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 結構 `dwKind` 。

`addr.addrMethod`\
[僅限 c + +]如果 = ADDRESS_KIND_METHOD，則包含[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 結構 `dwKind` 。

`addr.addrField`\
[僅限 c + +]如果 = ADDRESS_KIND_FIELD，則包含[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 結構 `dwKind` 。

`addr.addrLocal`\
[僅限 c + +]如果 = ADDRESS_KIND_LOCAL，則包含[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 結構 `dwKind` 。

`addr.addrParam`\
[僅限 c + +]如果 = ADDRESS_KIND_PARAM，則包含[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 結構 `dwKind` 。

`addr.addrArrayElem`\
[僅限 c + +]如果 = ADDRESS_KIND_ARRAYELEM，則包含[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 結構 `dwKind` 。

`addr.addrRetVal`\
[僅限 c + +]如果 = ADDRESS_KIND_RETVAL，則包含[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 結構 `dwKind` 。

`addr.unused`\
[僅限 c + +] 填補。

`addr`\
[僅限 c + +]聯集的名稱。

`unionmember`\
[僅限 c #]此值必須根據來封送處理至適當的結構類型 `dwKind` 。 請參閱與等位的關聯性的備註 `dwKind` 。

## <a name="remarks"></a>備註
此結構是 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 結構的一部分，代表了許多不同類型的位址， (`DEBUG_ADDRESS` 結構會藉由呼叫 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 方法) 來填入。

 [僅限 c #]下表說明如何解讀 `unionmember` 每種地址的成員。 此範例會示範如何針對一種位址進行這項操作。

|`dwKind`|`unionmember` 解釋為|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>範例
此範例示範如何 `METADATA_ADDRESS_ARRAYELEM` 在 c # 中解讀一種位址 () `DEBUG_ADDRESS_UNION` 結構。 其餘的元素可以用完全相同的方式來解讀。

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
