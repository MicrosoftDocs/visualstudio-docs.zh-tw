---
title: IDebugEngineProgram2:::觀看線程步驟 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730350"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
監視在給定線程上執行(或停止監視執行)。

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
[在][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示正在步進的程式。

`dwTid`\
[在]指定要監視的線程的標識碼。

`fWatch`\
[在]非零 ()`TRUE`表示開始`dwTid`在所標識的線程上監視執行。否則,零`FALSE`() 表示停止`dwTid`監視在執行 。

`dwFrame`\
[在]指定控制步驟類型的幀索引。 當此值為零(0)時,步驟類型為"進入",每當執行標識`dwTid`的線程時,程式都應停止。 當`dwFrame`是非零時,步驟類型為"步長",並且僅當`dwTid`標識 的線程在堆疊上的索引等於`dwFrame`或高於 的幀中運行時,程式才應停止。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當會話調試管理器 (SDM)`pOriginatingProgram`步步由 參數標識的程式時,它會通過調用此方法通知所有其他附加的程式。

 此方法僅適用於同一線程步進。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
