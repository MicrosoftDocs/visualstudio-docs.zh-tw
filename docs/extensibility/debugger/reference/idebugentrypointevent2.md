---
title: IDebugentryPoint事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531ff846f2488193ed7f3d9f200a1a4ea04df6f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730326"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
當程式即將執行其用戶代碼的第一個指令時,調試引擎 (DE) 會將此介面發送到工作階段調試管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面作為其正常操作的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。

## <a name="notes-for-callers"></a>通話備註
 當正在除錯的程式已載入並準備執行用戶代碼的第一個指令時,DE 將創建並發送此事件物件。 該事件使用 SDM 在連接到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="remarks"></a>備註
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)在程式即將執行第一個指令時發送。 例如,`IDebugEntryPoint2`在程式即將執行`main`使用者函數時發送。

 當`IDebugEntryPointEvent2`DE 傳送 時,目前代碼位置應位於使用者代碼的第`main`一個指令, 如 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
