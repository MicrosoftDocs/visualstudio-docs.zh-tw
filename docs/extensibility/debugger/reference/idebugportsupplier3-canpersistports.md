---
description: 此方法會決定埠供應商是否可以透過將埠寫入至磁片) ，以在偵錯工具的調用之間 (保存埠。
title: IDebugPortSupplier3：： CanPersistPorts |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 570409a114acbf19697b0eb3ef3e5496fdfde93a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071970"
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
