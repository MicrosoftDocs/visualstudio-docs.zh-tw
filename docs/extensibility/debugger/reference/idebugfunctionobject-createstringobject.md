---
title: IDebug函數物件::創建字串物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40a13b9b388caa6a1ae6e3e470e4ea02553fa0ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728525"
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
[在]字串物件的字串值。

`ppObject`\
[出]傳回表示新的建立的字串物件的[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 呼叫此方法以建立一個物件,該物件表示一個字串,該字串是[IDebug 函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面表示的函數的參數。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
