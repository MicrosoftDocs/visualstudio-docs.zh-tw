---
title: IDebug記憶位元組2::獲取大小 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de4eccb395059112dde40af36ce75798db9064b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727554"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
檢索此[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件表示的記憶體的大小(以位元組為單位)。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize( 
   UINT64* pqwSize
);
```

```csharp
int GetSize(
   out ulong pqwSize
);
```

## <a name="parameters"></a>參數
`pqwSize`\
[出]返回記憶體空間的大小(以位元組為單位)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
