---
title: IDebug函數物件::創建對象無構造函數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728569"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
創建沒有構造函數的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>參數
`pClassObject`\
[在]表示要創建的物件類型的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

`ppObject`\
[出]返回表示新創建物件的[IDebugObject。](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 呼叫此方法以建立表示結構或複雜類型的實例的物件(不需要建構函數),該實例是[IDebugAtheObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面表示的函數的參數。

 如果物件參數需要建構函數,請呼叫[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
