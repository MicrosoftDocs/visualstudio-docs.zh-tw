---
description: 這個方法會取得進程目前的 [編輯後繼續] 狀態。
title: IDebugProcess3：： GetENCAvailableState |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c851689d9e47250457c93d1621acb6c5db98732b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081551"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
這個方法會取得進程目前的 [編輯後繼續] 狀態。 自訂埠供應商應該一律傳回 `E_NOTIMPL` 。

## <a name="syntax"></a>語法

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>參數
`pReason`\
擴展來自 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 列舉的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

> [!NOTE]
> 自訂埠供應商應該一律傳回 `E_NOTIMPL` 。

## <a name="remarks"></a>備註
 此狀態可能受 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)影響。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
