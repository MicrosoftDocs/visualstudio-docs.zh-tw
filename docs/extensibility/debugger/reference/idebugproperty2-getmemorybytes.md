---
title: IDebug屬性2::獲取內存位元組 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d13fa3821a6d7bf861cd160a5588d0788b92243
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721473"
---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
獲取構成屬性值的記憶體位元組。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMemoryBytes ( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes ( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>參數
`ppMemoryBytes`\
[出]返回可用於檢索包含屬性值的記憶體的[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。 如果沒有`S_GETMEMORYBYTES_NO_MEMORY_BYTES`要檢索的記憶體位元組,則返回。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
