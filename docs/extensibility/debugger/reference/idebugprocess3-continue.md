---
title: IDebugProcess3::繼續 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723776"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
繼續從已停止狀態運行此過程。 保留任何以前的執行狀態(如步驟),進程將再次開始執行。

> [!NOTE]
> 此方法應使用而不是["繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)」。

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
`pThread`\
[在]表示要繼續的線程的[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 無論正在調試的進程數或哪個進程生成了停止事件,此過程都會調用此方法。 實現必須保留以前的執行狀態(如步驟),並繼續執行,就好像在完成之前執行之前從未停止過一樣。 也就是說,如果此過程中的線程執行過單操作,並且由於其他進程停止而停止,然後`Continue`被調用,則指定的線程必須完成原始跨行操作。

 **警告**在處理此調用時,不要向[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件或立即(同步)事件;否則調試器可能會掛起。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
