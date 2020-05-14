---
title: OBJECT_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714135"
---
# <a name="object_type"></a>Object_Type
從表達式賦值器指定對象的類型。

## <a name="syntax"></a>語法

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>欄位
 `OBJECT_TYPE_BOOLEAN`\
 指示對像是布爾。

 `OBJECT_TYPE_CHAR`\
 指示對像是字元。

 `OBJECT_TYPE_I1`\
 指示對像是一位節簽名整數。

 `OBJECT_TYPE_U1`\
 指示該對像是一個無符號整數。

 `OBJECT_TYPE_I2`\
 指示對像是兩位元節簽名整數。

 `OBJECT_TYPE_U2`\
 指示該對像是一個兩位元組的無符號整數。

 `OBJECT_TYPE_I4`\
 指示對像是四位元節簽名整數。

 `OBJECT_TYPE_U4`\
 指示該對像是一個四位元組的無符號整數。

 `OBJECT_TYPE_I8`\
 指示該對像是一個八位元節簽名整數。

 `OBJECT_TYPE_U8`\
 指示該對像是一個八位元組的無符號整數。

 `OBJECT_TYPE_R4`\
 指示物件是四位元組浮點數。

 `OBJECT_TYPE_R8`\
 指示對像是八位元組浮點數。

 `OBJECT_TYPE_OBJECT`\
 指示對像是物件。

 `OBJECT_TYPE_NULL`\
 指示物件為 NULL。

 `OBJECT_TYPE_CLASS`\
 指示對像是類。

## <a name="remarks"></a>備註
 作為參數傳遞給 Create[原始物件](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)和[創建 ArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)方法。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
