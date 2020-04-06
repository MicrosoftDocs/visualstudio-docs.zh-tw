---
title: IDebug函數物件::創建ArrayObject |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728611"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
創建陣列物件。 此陣列可以包含基元或物件實例值。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>參數
`ot`\
[在]指定[OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)枚舉中的值,指示新陣組物件的類型。

`pClassField`\
[在]如果創建物件實例值陣列,則表示物件的類的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。 如果創建基元物件的陣列,則此參數為空值。

`dwRank`\
[在]陣列的級別或維度數。

`dwDims`\
[在]陣列的每個維度的大小。

`dwLowBounds`\
[在]每個維度(通常為 0 或 1)的原點。

`ppObject`\
[出]傳回表示新的建立的陣列的[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)。 這實際上是一個[IDebugArray 物件](../../../extensibility/debugger/reference/idebugarrayobject.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 調用此方法以創建一個物件,該物件表示由[IDebug函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面表示的函數的陣列參數。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
