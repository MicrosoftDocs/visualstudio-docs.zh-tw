---
title: DEBUG_ADDRESS_UNION |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737535"
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
[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚舉中的值,指定如何解釋聯合。

`addr.addrNative`\
[僅C++]如果[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)=`dwKind`ADDRESS_KIND_NATIVE, 則包含NATIVE_ADDRESS結構。

`addr.addrThisRel`\
[僅C++]如果[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)=`dwKind`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE, 則包含UNMANAGED_ADDRESS_THIS_RELATIVE結構。

`addr.addUPhysical`\
[僅C++]如果[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)=`dwKind`ADDRESS_KIND_UNMANAGED_PHYSICAL, 則包含UNMANAGED_ADDRESS_PHYSICAL結構。

`addr.addrMethod`\
[僅C++]如果[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)=`dwKind`ADDRESS_KIND_METHOD, 則包含METADATA_ADDRESS_METHOD結構。

`addr.addrField`\
[僅C++]如果[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)=`dwKind`ADDRESS_KIND_FIELD, 則包含METADATA_ADDRESS_FIELD結構。

`addr.addrLocal`\
[僅C++]如果[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)=`dwKind`ADDRESS_KIND_LOCAL, 則包含METADATA_ADDRESS_LOCAL結構。

`addr.addrParam`\
[僅C++]如果[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)=`dwKind`ADDRESS_KIND_PARAM, 則包含METADATA_ADDRESS_PARAM結構。

`addr.addrArrayElem`\
[僅C++]如果[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)=`dwKind`ADDRESS_KIND_ARRAYELEM, 則包含METADATA_ADDRESS_ARRAYELEM結構。

`addr.addrRetVal`\
[僅C++]如果[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)=`dwKind`ADDRESS_KIND_RETVAL, 則包含METADATA_ADDRESS_RETVAL結構。

`addr.unused`\
[僅C++] 填充。

`addr`\
[僅C++]聯合的名稱。

`unionmember`\
[僅 C]此值需要根據`dwKind`進行封送到相應的結構類型。 有關聯合之間的`dwKind`關聯和解釋,請參閱備註。

## <a name="remarks"></a>備註
此結構是[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構的一部分,表示多種不同類型的位址之`DEBUG_ADDRESS`一( 結構由對[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法的調用填充)。

 [僅 C]下表顯示了如何解釋每種地址`unionmember`的成員。 "範例"顯示了如何針對一種位址執行此操作。

|`dwKind`|`unionmember`解釋為|
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
此範例展示如何解釋 C# 中`METADATA_ADDRESS_ARRAYELEM``DEBUG_ADDRESS_UNION`結構的位址 ( ) 。 其餘元素的解釋方式完全相同。

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

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
