---
description: 這個方法會傳回目前 IDebugObjects 列舉的複本作為個別的物件。
title: IEnumDebugObjects：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Clone
helpviewer_keywords:
- IEnumDebugObjects::Clone method
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64d8b862de9f068b41a9fc752855b6affa310298
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083059"
---
# <a name="ienumdebugobjectsclone"></a>IEnumDebugObjects::Clone
這個方法會傳回目前列舉的複本，做為個別的物件。

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
擴展傳回這個列舉的複本作為個別的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的複本在呼叫這個方法時，的狀態與原始的相同。 不過，複本和原始的狀態是分開的，而且可以個別變更。

## <a name="see-also"></a>另請參閱
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
