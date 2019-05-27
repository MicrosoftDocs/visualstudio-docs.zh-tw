---
title: IEnumDebugAddresses::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Clone
helpviewer_keywords:
- IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7be8c22896759ec32fe595965c2e62c9c63ac01
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203625"
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
這個方法會傳回一份目前的列舉，為個別的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumDebugAddresses** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugAddresses ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[out]傳回這個列舉型別為個別物件的複本。

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的複本會呼叫這個方法只有在有相同的原始狀態。 不過，複本與原始的狀態是分開的而且可以個別變更。

## <a name="see-also"></a>另請參閱
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)