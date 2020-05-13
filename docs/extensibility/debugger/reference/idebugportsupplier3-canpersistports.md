---
title: IDebugPort供應商3:::Can堅持埠 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724470"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
此方法確定埠供應商是否可以在調試器的調用之間(通過將它們寫入磁碟)持久化埠。

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
 `S_OK`如果可以保留埠,或`S_FALSE`指示無法保留埠。

## <a name="remarks"></a>備註
 如果埠供應商可以保留埠,則應在埠被銷毀時執行此操作,然後在再次實例化埠時重新載入它們。

## <a name="see-also"></a>另請參閱
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
