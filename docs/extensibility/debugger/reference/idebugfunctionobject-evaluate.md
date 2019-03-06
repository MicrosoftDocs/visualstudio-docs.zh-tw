---
title: IDebugFunctionObject::Evaluate |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9deaf32a88d476895feab006cbe3b818d11b97ca
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685336"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
呼叫函式，並傳回產生的值當做物件。

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

#### <a name="parameters"></a>參數
 `ppParams`

 [in]陣列[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)代表輸入的參數的物件。 每個參數經由之一`Create`中的方法[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。

 `dwParams`

 [in]中的參數數目`ppParams`陣列。

 `dwTimeout`

 [in]指定的時間上限，以毫秒為單位，從這個方法返回之前等候。 使用`INFINITE`無限期等候。

 `ppResult`

 [out]傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)表示函式物件的值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會設定並執行所表示之函式呼叫[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)