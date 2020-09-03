---
title: IDebugStackFrame2：： GetPhysicalStackRange |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719665"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
取得與堆疊框架相關聯之實體位址範圍的電腦相依標記法。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>參數
`paddrMin`\
擴展傳回與這個堆疊框架相關聯的最低實體位址。

`paddrMax`\
擴展傳回與這個堆疊框架相關聯的最高實體位址。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 此方法所傳回的資訊是由會話 debug manager (SDM) 用來排序堆疊框架。

 假設呼叫堆疊會逐漸減少，也就是新的堆疊框架會在越來越低的記憶體位址中新增。 執行時間架構必須提供符合此假設的實體堆疊範圍。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
