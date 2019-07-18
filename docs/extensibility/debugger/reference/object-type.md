---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 726e4978ac2c474b1f23b90f409f25b8a58aceab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349923"
---
# <a name="objecttype"></a>OBJECT_TYPE
指定運算式評估工具中的物件的類型。

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
 指出物件是布林值。

 `OBJECT_TYPE_CHAR`\
 指出物件是一個字元。

 `OBJECT_TYPE_I1`\
 指出物件是一個位元組帶正負號的整數。

 `OBJECT_TYPE_U1`\
 指出物件是一個位元組不帶正負號的整數。

 `OBJECT_TYPE_I2`\
 指出物件是二位元組帶正負號的整數。

 `OBJECT_TYPE_U2`\
 指出物件是二位元組不帶正負號的整數。

 `OBJECT_TYPE_I4`\
 指出物件是四位元組帶正負號的整數。

 `OBJECT_TYPE_U4`\
 指出物件是四位元組不帶正負號的整數。

 `OBJECT_TYPE_I8`\
 表示此物件是八位元組帶正負號的整數。

 `OBJECT_TYPE_U8`\
 表示物件的八位元組不帶正負號的整數。

 `OBJECT_TYPE_R4`\
 指出物件是四位元組浮點數。

 `OBJECT_TYPE_R8`\
 指出物件是 8 位元組浮點數。

 `OBJECT_TYPE_OBJECT`\
 表示物件的物件。

 `OBJECT_TYPE_NULL`\
 表示為 NULL 的物件。

 `OBJECT_TYPE_CLASS`\
 表示物件的類別。

## <a name="remarks"></a>備註
 作為引數[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)並[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)方法。

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)