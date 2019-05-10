---
title: IEnumDebugObjects::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 786adff86b35ed4d33b07a4144544adffe53ea75
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226456"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
這個方法會將列舉重設第一個項目。

## <a name="syntax"></a>語法

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>參數
 None

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法是，下一個呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)傳回列舉的第一個項目。

## <a name="see-also"></a>另請參閱
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)