---
title: IEnumDebugObjects::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Clone
helpviewer_keywords:
- IEnumDebugObjects::Clone method
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76ae819deecaa76d37054235b6bed295278ca37d
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223450"
---
# <a name="ienumdebugobjectsclone"></a>IEnumDebugObjects::Clone
這個方法會傳回一份目前的列舉，為個別的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT Clone(
   IEnumDebugObjects** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>參數
 `ppEnum`\

 [out]傳回這個列舉型別為個別物件的複本。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的複本會呼叫這個方法只有在有相同的原始狀態。 不過，複本與原始的狀態是分開的而且可以個別變更。

## <a name="see-also"></a>另請參閱
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)