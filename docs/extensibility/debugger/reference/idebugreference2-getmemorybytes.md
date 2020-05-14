---
title: IDebug參考2::獲取內存位元組 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryBytes
helpviewer_keywords:
- IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 958c38d6650c7152efef9fe72481a46a70090660
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720607"
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
獲取物理包含引用值的記憶體位元組。 保留供未來使用。

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
[出]返回可用於檢索包含引用值的記憶體的[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件。

## <a name="return-value"></a>傳回值
 永遠會傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
