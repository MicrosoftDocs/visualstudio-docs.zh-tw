---
title: IEnumDebugObjects::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5a9e8e08c19e7d4f2a8b47ad0124115743522a8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339541"
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