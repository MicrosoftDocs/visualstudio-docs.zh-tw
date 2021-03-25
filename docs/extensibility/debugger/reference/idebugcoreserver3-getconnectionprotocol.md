---
description: 傳回值，這個值表示要用來在伺服器與 debug 封裝之間進行通訊的通訊協定。
title: IDebugCoreServer3：： GetConnectionProtocol |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18df64ad156c6eb81f51b0504b4d65514b168abe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077651"
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
傳回值，這個值表示要用來在伺服器與 debug 封裝之間進行通訊的通訊協定。

## <a name="syntax"></a>語法

```cpp
HRESULT GetConnectionProtocol(
   CONNECTION_PROTOCOL* pProtocol
);
```

```csharp
int GetConnectionProtocol(
   CONNECTION_PROTOCOL[] pProtocol
);
```

## <a name="parameters"></a>參數
`pProtocol`\
擴展傳回 [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) 列舉中的其中一個值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)
