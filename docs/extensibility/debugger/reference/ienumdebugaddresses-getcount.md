---
title: IEnumDebugAddresses::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21d722c557d6dc7dcb250b88abcebdf771af8647
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716778"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
這個方法會傳回在列舉中的項目數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

#### <a name="parameters"></a>參數
 `pcelt`

 [out]列舉中傳回的項目數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法不是指定只有下一步、 複製、 Skip 和重設需要實作的自訂 COM 列舉型別介面的一部分。

## <a name="see-also"></a>另請參閱
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)