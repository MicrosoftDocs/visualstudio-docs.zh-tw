---
description: 傳回屬性值的參考。
title: IDebugProperty2：： GetReference |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c103e8826266ddbaaa5b96f4a9aa32067893e45f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166783"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
傳回屬性值的參考。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>參數
`ppRererence`\
擴展傳回 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 物件，代表屬性值的參考。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼，通常是 `E_NOTIMPL` 或 `E_GETREFERENCE_NO_REFERENCE` 。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
