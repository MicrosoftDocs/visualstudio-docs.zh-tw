---
description: 這個方法會將位址列舉重設為第一個元素。
title: IEnumDebugAddresses：： Reset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 385e650e908947288eafa6f3f2812db45f9721a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083137"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
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
 呼叫這個方法之後， [下一次](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) 呼叫會傳回列舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
