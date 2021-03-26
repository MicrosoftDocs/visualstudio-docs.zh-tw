---
description: 指定位址的種類。
title: ADDRESS_KIND |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca55e3de468ed61a3af32ddfe99873b90013aa16
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085503"
---
# <a name="address_kind"></a>ADDRESS_KIND
指定位址的種類。

## <a name="syntax"></a>Syntax

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>欄位
`ADDRESS_KIND_NATIVE`\
原生位址，以 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 結構表示。

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
相對於 `this` Visual Basic) 指標中 (的非受控位址 `Me` ，並以 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 結構表示。

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
未受管理的實體位址，以 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 結構表示。

`ADDRESS_KIND_METHOD`\
類別的方法，以 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 結構表示。

`ADDRESS_KIND_FIELD`\
類別的欄位，以 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 結構表示。

`ADDRESS_KIND_LOCAL`\
位址適用于本機變數，並由 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 結構表示。

`ADDRESS_KIND_PARAM`\
方法或函數參數，以 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 結構表示。

`ADDRESS_KIND_ARRAYELEM`\
陣列元素，以 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 結構表示。

`ADDRESS_KIND_RETVAL`\
傳回值，以 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 結構表示。

## <a name="remarks"></a>備註
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法會傳回[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構，其中包含可能結構的聯集，也就是[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構。 `dwKind`結構的欄位會 `DEBUG_ADDRESS_UNION` 保存 `ADDRESS_KIND` 值，並描述如何解讀聯集欄位。

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
