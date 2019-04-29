---
title: IDebugMemoryBytes2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbed7e4421b01e1a779c5c976001a5dd5b4ba2d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918889"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
擷取的大小，以位元組為單位所表示的記憶體[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件。

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

#### <a name="parameters"></a>參數
 `pqwSize`

 [out]傳回大小，以位元組為單位的記憶體空間。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)