---
description: 傳回結構，描述物件與其在其範圍或容器內的位置。
title: IDebugAddress：： GetAddress |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094391"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
傳回結構，描述物件與其在其範圍或容器內的位置。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>參數
`pAddress`\
[in，out]由這個方法填入的 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構會傳遞給這個方法，然後將其填入適當的資訊。 這項資訊的解讀方式取決於傳回的資訊類型，以及符號處理常式本身。 如需詳細資訊，請參閱 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 。

## <a name="see-also"></a>另請參閱
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
