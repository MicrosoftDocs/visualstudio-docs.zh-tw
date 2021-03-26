---
description: 這個方法會將列舉重設為第一個 IDebugObject 元素。
title: IEnumDebugObjects：： Reset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 193f0f2f793c1ca1ee1af208105be33754a1effa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083046"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
這個方法會將列舉重設為第一個元素。

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
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法之後， [下一次](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) 呼叫會傳回列舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
