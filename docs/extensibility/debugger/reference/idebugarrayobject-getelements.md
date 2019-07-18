---
title: IDebugArrayObject::GetElements |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 915724fa5790c6b8c9fde2706b1222db239cb4ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351787"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
取得陣列的所有項目的列舉程式。

## <a name="syntax"></a>語法

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[out]傳回[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)物件，可讓您列舉所有的項目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="remarks"></a>備註
 或者，使用[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)並[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)方法來逐一查看項目。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)