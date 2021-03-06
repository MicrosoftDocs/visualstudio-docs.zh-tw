---
description: 從運算式評估工具指定物件的類型。
title: OBJECT_TYPE |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3add4d46a258eb7e6c107f8d2eb16f7cd84ba919
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222155"
---
# <a name="object_type"></a>Object_Type
從運算式評估工具指定物件的類型。

## <a name="syntax"></a>Syntax

```cpp
enum enum_OBJECT_TYPE { 
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
public enum enum_OBJECT_TYPE { 
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
 指出物件是布林值。

 `OBJECT_TYPE_CHAR`\
 表示物件為字元。

 `OBJECT_TYPE_I1`\
 指出物件是一個位元組帶正負號的整數。

 `OBJECT_TYPE_U1`\
 指出物件是一個位元組不帶正負號的整數。

 `OBJECT_TYPE_I2`\
 指出物件是雙位元組帶正負號的整數。

 `OBJECT_TYPE_U2`\
 指出物件是雙位元組不帶正負號的整數。

 `OBJECT_TYPE_I4`\
 指出物件是四位元組帶正負號的整數。

 `OBJECT_TYPE_U4`\
 表示物件為四位元組不帶正負號的整數。

 `OBJECT_TYPE_I8`\
 指出物件是八位元組帶正負號的整數。

 `OBJECT_TYPE_U8`\
 指出物件是八位元組不帶正負號的整數。

 `OBJECT_TYPE_R4`\
 指出物件是四位元組浮點數。

 `OBJECT_TYPE_R8`\
 指出物件是八位元組浮點數。

 `OBJECT_TYPE_OBJECT`\
 表示物件是物件。

 `OBJECT_TYPE_NULL`\
 表示物件為 Null。

 `OBJECT_TYPE_CLASS`\
 表示物件為類別。

## <a name="remarks"></a>備註
 以引數形式傳遞至 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) 和 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) 方法。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
