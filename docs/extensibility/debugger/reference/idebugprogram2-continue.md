---
title: IDebugProgram2::繼續 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723072"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
繼續從已停止狀態運行此程式。 保留任何以前的執行狀態(如步驟),程式將再次開始執行。

> [!NOTE]
> 此方法已被取代。 請改用["繼續"](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

## <a name="syntax"></a>語法

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>參數
`pThread`[在]表示線程的[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 無論正在調試的程式數或哪個程式生成停止事件,此程序都會調用此方法。 實現必須保留以前的執行狀態(如步驟),並繼續執行,就好像在完成之前執行之前從未停止過一樣。 也就是說,如果此程式中的線程執行過單操作,並且由於其他程式停止而停止,然後調用此方法,則程式必須完成原始跨行操作。

> [!WARNING]
> 在處理此調用時,不要向[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件或立即(同步)事件;否則調試器可能會掛起。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
