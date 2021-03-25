---
description: 這個方法會取得此埠的 IDebugPortNotify2 介面。
title: IDebugDefaultPort2：： GetPortNotify |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077469"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
這個方法會取得此埠的 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 介面。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>參數
`ppPortNotify`\
擴展 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 一般來說， `QueryInterface` 方法是在執行 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 介面的物件上呼叫，以取得 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) 介面。 不過，在某些情況下，會在不同的物件上執行所需的介面。 這個方法會隱藏這些情況，並 `IDebugPortNotify2` 從最適當的物件傳回介面。

## <a name="see-also"></a>另請參閱
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
