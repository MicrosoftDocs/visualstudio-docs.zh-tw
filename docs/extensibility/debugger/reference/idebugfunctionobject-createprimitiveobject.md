---
title: IDebug函數物件::創建原始物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728528"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
創建基元數據物件,如簡單整數。

## <a name="syntax"></a>語法

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>參數
`ot`\
[在]OBJECT_TYPE[枚舉](../../../extensibility/debugger/reference/object-type.md)的值,表示要創建的基元類型。

`ppObject`\
[出]返回表示新創建物件的[IDebugObject。](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 調用此方法以創建一個物件,該物件表示由[IDebug函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面表示的函數的參數。 例如,如果表達式字串為"myString(5)",則此方法將用於創建表示整數 5 的物件。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
