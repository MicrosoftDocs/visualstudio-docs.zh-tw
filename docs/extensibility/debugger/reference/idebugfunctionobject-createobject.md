---
title: IDebug函數物件::創建物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728592"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
使用構造函數創建物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>參數
`pConstructor`\
[在][IDebug函數物件物件](../../../extensibility/debugger/reference/idebugfunctionobject.md),表示要創建的對象的構造函數。

`dwArgs`\
[在]陣列中的`pArg`參數數。 表示傳遞給構造函數的參數數。

`pArg`\
[在][IDebugObject 物件的](../../../extensibility/debugger/reference/idebugobject.md)陣列,表示傳遞給建構函數的參數。

`ppObject`\
[出]返回表示`IDebugObject`新創建的物件。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 調用此方法以創建一個物件,該物件表示類(或需要構造函數的其他複雜類型)的實例,該實例是[iDebug 函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面表示的函數的參數。

 如果物件參數不需要建構函數,請調用[CreateObjectNo構造函數](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
