---
title: IDebug函數物件2::創建物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728487"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
創建使用建構函數給定評估標誌設置和超時值的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>參數
`pConstructor`\
[在]表示要建立物件的建構函數的[IDebug 函式物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)。

`dwArgs`\
[在]陣列中的`pArg`參數數。 表示傳遞給構造函數的參數數。

`pArgs`\
[在][IDebugObject 物件的](../../../extensibility/debugger/reference/idebugobject.md)陣列,表示傳遞給建構函數的參數。

`dwEvalFlags`\
[在][EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉中的標誌組合,用於指定如何執行計算。

`dwTimeout`\
[在]從此方法返回之前等待的最大時間(以毫秒為單位)。 使用**INFINITE**無限期等待。

`ppObject`\
[出]返回表示新創建物件的**IDebugObject。**

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 調用此方法以創建表示類實例的物件,或需要構造函數(即參數)的其他複雜類型。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
