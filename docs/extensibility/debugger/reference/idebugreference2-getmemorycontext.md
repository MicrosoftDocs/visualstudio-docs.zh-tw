---
description: 取得參考的記憶體內容。
title: IDebugReference2：： GetMemoryCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac7cb401df9382aa3951e67bde0edf58bb905a3d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071401"
---
# <a name="idebugreference2getmemorycontext"></a>IDebugReference2::GetMemoryContext
取得參考的記憶體內容。 保留供未來使用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext ( 
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>參數
`ppMemory`\
擴展傳回 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件，代表與參考值相關聯的記憶體。

## <a name="return-value"></a>傳回值
 一律傳回 `E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
