---
title: IDebugStackFrame3：： GetUnwindCodeCoNtext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3cb8d468971a578f68ba64fe754ed788493400a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934047"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
如果發生堆疊回溯作業，則傳回代表位置的程式碼內容。

## <a name="syntax"></a>語法

```cpp
HRESULT GetUnwindCodeContext(
   IDebugCodeContext2 **ppCodeContext
);
```

```csharp
int GetUnwindCodeContext(
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>參數
`ppCodeContext`\
擴展傳回 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件，這個物件表示發生堆疊回溯時的程式碼內容位置。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 雖然此方法可能會在堆疊回溯之後傳回位置的程式碼內容，但不一定表示堆疊回溯實際上可以出現在目前的堆疊框架中。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
