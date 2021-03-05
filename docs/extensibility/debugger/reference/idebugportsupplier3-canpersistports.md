---
description: 此方法會決定埠供應商是否可以透過將埠寫入至磁片) ，以在偵錯工具的調用之間 (保存埠。
title: IDebugPortSupplier3：： CanPersistPorts |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172005"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
此方法會決定埠供應商是否可以透過將埠寫入至磁片) ，以在偵錯工具的調用之間 (保存埠。

## <a name="syntax"></a>語法

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 `S_OK` 如果可以保存埠，或 `S_FALSE` 表示無法保存埠。

## <a name="remarks"></a>備註
 如果埠供應商可保存埠，則它應該在終結時這麼做，然後在具現化時重載它們。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
