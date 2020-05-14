---
title: IDebugThread2::設置下一個語句 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718659"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
將當前指令指標設置到給定的代碼上下文。

## <a name="syntax"></a>語法

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>參數
`pStackFrame`\
保留供將來使用;設置為空值。

`pCodeContext`\
[在][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件,用於描述即將執行的代碼位置及其上下文。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 下表顯示了其他可能的值。

|值|描述|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|下一個語句不能位於幀堆疊的更深的堆疊框架中。|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|下一個語句不與堆疊中的任何幀相關聯。|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|某些調試引擎無法在異常之後設置下一個語句。|

## <a name="remarks"></a>備註
 指令指標指示要執行的下一個指令或語句。 此方法用於重試一行原始碼或強制執行以在另一個函數中繼續執行,例如。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
