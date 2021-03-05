---
description: 建立陣列物件。
title: IDebugFunctionObject：： CreateArrayObject |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aee0617364321e5a18f0ea83ef7f19f1388209df
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166485"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
建立陣列物件。 這個陣列可以包含基本或物件實例值。

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
在指定 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 列舉中的值，表示新陣列物件的型別。

`pClassField`\
在代表物件之類別的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件（如果建立物件實例值的陣列）。 如果建立基本物件的陣列，此參數為 null 值。

`dwRank`\
在陣列的等級或維度數目。

`dwDims`\
在陣列的每個維度大小。

`dwLowBounds`\
在每個維度的來源 (通常是0或 1) 。

`ppObject`\
擴展傳回代表新建立之陣列的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件。 這實際上是 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法來建立物件，該物件代表 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面所代表之函式的陣列參數。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
