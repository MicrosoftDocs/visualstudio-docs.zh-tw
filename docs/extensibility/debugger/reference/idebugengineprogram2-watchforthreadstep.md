---
description: 監看執行 (或停止監看執行) 發生在指定的執行緒上。
title: IDebugEngineProgram2：： WatchForThreadStep |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaf02e07bebbbfd711d99ef7605befbdce1f9376
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153413"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
監看執行 (或停止監看執行) 發生在指定的執行緒上。

## <a name="syntax"></a>語法

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>參數
`pOriginatingProgram`\
在代表正在逐步進行程式的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件。

`dwTid`\
在指定要監看之執行緒的識別碼。

`fWatch`\
在非零的 (`TRUE`) 表示在所識別的執行緒上開始監看執行 `dwTid` ; 否則，零 (`FALSE`) 表示停止監看的執行 `dwTid` 。

`dwFrame`\
在指定控制步驟類型的框架索引。 當此值為零時 (0) 時，步驟類型會是「逐步執行」，且程式應在每次由所識別的執行緒執行時停止 `dwTid` 。 當 `dwFrame` 為非零時，步驟類型會是「不進入進程」，且只有在所識別的執行緒 `dwTid` 是在堆疊上的索引等於或高於的框架中執行時，才會停止程式 `dwFrame` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當會話 debug manager (SDM) 逐步執行程式時，由參數所識別 `pOriginatingProgram` ，它會藉由呼叫這個方法來通知所有其他附加的程式。

 這個方法僅適用于相同執行緒逐步執行。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
