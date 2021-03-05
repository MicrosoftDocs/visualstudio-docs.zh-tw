---
description: 將目前的指令指標設定為指定的程式碼內容。
title: IDebugThread2：： SetNextStatement |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d29b351662ce5cb8aeda9a1f65e278349a0a3b18
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164470"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
將目前的指令指標設定為指定的程式碼內容。

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
保留供日後使用;設定為 null 值。

`pCodeContext`\
在 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件，描述要執行的程式碼位置及其內容。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 下表顯示其他可能的值。

|值|描述|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|下一個語句不能在堆疊框架中更深入的框架堆疊。|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|下一個語句與堆疊中的任何框架沒有關聯。|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|某些偵錯工具引擎無法在例外狀況之後設定下一個語句。|

## <a name="remarks"></a>備註
 指令指標表示要執行的下一個指令或語句。 例如，這個方法可用來重試一行原始程式碼或強制繼續執行另一個函式。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
