---
title: IDebugThread2::可以設置下一個語句 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4232c25bfe9acd7f17c88c28aa4211a9c62175f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718848"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
確定當前指令指標是否可以設置為給定的堆疊幀。

## <a name="syntax"></a>語法

```cpp
HRESULT CanSetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int CanSetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>參數
`pStackFrame`\
保留供將來使用;設置為空值。 如果這是空值,請使用當前堆疊幀。

`pCodeContext`\
[在][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件,用於描述即將執行的代碼位置及其上下文。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果此方法返回`S_OK`,則調用[SetNext語句](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)方法以實際設置下一個語句。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
