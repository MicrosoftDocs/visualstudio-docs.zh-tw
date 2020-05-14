---
title: IDebugStackFrame3::獲取解說碼上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 488f675c39bb01c87aca13a9bef8cc4a715ecf18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719493"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
如果發生堆疊展開操作,則返回表示位置的代碼上下文。

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
[出]返回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件,該物件表示發生堆疊展開時的代碼上下文位置。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 儘管此方法可能在堆疊展開后返回位置的代碼上下文,但這並不一定意味著堆疊展開實際上可能發生在當前堆疊幀中。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
