---
description: 抓取這個 IDebugMemoryBytes2 物件所表示之記憶體的大小（以位元組為單位）。
title: IDebugMemoryBytes2：： GetSize |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c76b9061bd5b54e222f7092720e29805aba028b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076780"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
抓取這個 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 物件所表示之記憶體的大小（以位元組為單位）。

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
擴展傳回記憶體空間的大小（以位元組為單位）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
