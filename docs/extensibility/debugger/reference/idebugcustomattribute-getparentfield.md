---
description: 取得附加自訂屬性的欄位。
title: IDebugCustomAttribute：： GetParentField |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4af4569b64a41fc84a09c7e8f2ce0a8f6b42e86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154505"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
取得附加自訂屬性的欄位。

## <a name="syntax"></a>語法

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>參數
`ppField`\
擴展傳回 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件，代表要附加自訂屬性的欄位。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 在傳回的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件上呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法，以判斷父系的欄位類型。

## <a name="see-also"></a>另請參閱
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
