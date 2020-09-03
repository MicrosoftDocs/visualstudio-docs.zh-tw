---
title: IDebugPortSupplier3：： CanPersistPorts |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724470"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
此方法會決定埠供應商是否可以透過將埠寫入至磁片) ，以在偵錯工具的調用之間 (保存埠。

## <a name="syntax"></a>語法

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 `S_OK` 如果可以保存埠，或 `S_FALSE` 表示無法保存埠。

## <a name="remarks"></a>備註
 如果埠供應商可保存埠，則它應該在終結時這麼做，然後在具現化時重載它們。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
