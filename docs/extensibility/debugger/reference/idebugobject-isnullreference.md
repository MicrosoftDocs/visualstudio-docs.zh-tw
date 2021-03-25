---
description: 測試這個物件是否為 null 參考。
title: IDebugObject：： IsNullReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba037f995c97a3bfbf059f51bfb4f8777803a172
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054071"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
測試這個物件是否為 null 參考。

## <a name="syntax"></a>語法

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>參數
`pfIsNull`\
擴展 `TRUE` 如果此物件為 null 參考，則會傳回非零的 () ; 否則會傳回零 (`FALSE`) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 Null 參考表示空的物件或尚未指派給的物件。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
