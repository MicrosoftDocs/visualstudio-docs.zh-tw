---
description: 取得屬性值的記憶體內容。
title: IDebugProperty2：： GetMemoryCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35eff7948bc6171a0853f8772b65cf10c0b4cf1b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064965"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
取得屬性值的記憶體內容。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>參數
`ppMemory`\
擴展傳回 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 物件，代表與這個屬性相關聯的記憶體。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT`如果沒有要取出的記憶體內容，則會傳回。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
