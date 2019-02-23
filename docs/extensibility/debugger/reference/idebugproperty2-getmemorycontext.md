---
title: IDebugProperty2::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2db790564ed46a0add74552a8c691e92eb781855
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683777"
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

#### <a name="parameters"></a>參數
 `ppMemory`

 [out]傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，表示此屬性相關聯的記憶體。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT`如果沒有要擷取記憶體內容。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)