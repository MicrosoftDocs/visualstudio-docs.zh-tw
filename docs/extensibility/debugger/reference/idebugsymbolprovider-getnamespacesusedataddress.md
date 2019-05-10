---
title: IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc32ea0d07779f82bb741b99632ec16a950e5da2
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223969"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
這個方法會建立偵錯位址相關聯的命名空間的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetNamespacesUsedAtAddress( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetNamespacesUsedAtAddress(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
 `pAddress`\

 [in]偵錯位址。

 `ppEnum`\

 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)命名空間的列舉值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 可能有數個與指定的偵錯位址，例如，相關聯的命名空間巢狀命名空間或多個`using`陳述式。

## <a name="see-also"></a>另請參閱
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)