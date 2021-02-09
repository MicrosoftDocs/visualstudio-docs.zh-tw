---
title: IDebugFunctionObject：： CreateStringObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1fe290655781dd144e7c7b3951e021124e46086
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929949"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
建立字串物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>參數
`pcstrString`\
在字串物件的字串值。

`ppObject`\
擴展傳回代表新建立之字串物件的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法來建立物件，該物件代表 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面所代表的函式之參數的字串。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
