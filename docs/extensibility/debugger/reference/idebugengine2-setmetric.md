---
description: 這個方法會設定稱為度量的登錄值。
title: IDebugEngine2：： SetMetric |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 129067ab94c433b7c4b09e29c65d75df98ce6b68
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153881"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
這個方法會設定稱為度量的登錄值。

## <a name="syntax"></a>語法

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>參數
`pszMetric`\
在度量名稱。

`varValue`\
在指定度量值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 計量是一個登錄值，可用來變更 debug 引擎的行為或通告支援的功能。 這個方法可以將呼叫轉送至適當形式的 SDK helper， [以進行偵錯工具的](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 偵測功能 `SetMetric` 。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
