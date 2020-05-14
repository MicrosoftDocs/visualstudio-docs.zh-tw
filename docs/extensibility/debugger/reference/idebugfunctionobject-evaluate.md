---
title: IDebug函數物件::評估 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529a5f67c808efa258bc0cb9899f546dbb90d431
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728505"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
調用函數並將結果值作為物件返回。

## <a name="syntax"></a>語法

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>參數
`ppParams`\
[在]表示輸入參數的[IDebugObject 物件的](../../../extensibility/debugger/reference/idebugobject.md)陣列。 每個參數都是使用[IDebug 函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面中的`Create`一種方法創建的。

`dwParams`\
[在]陣列中的`ppParams`參數數。

`dwTimeout`\
[在]指定從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`ppResult`\
[出]返回表示函數值為物件的[IDebugObject。](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法設置並執行對[IDebug函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)表示的函數的調用。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
