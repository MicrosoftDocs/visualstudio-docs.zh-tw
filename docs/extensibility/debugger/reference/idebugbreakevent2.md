---
title: IDebugBreakevent2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735400"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
此介面告訴工作階段調試管理器 (SDM) 已成功完成非同步中斷。

## <a name="syntax"></a>語法

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以支援程式中的用戶中斷。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

## <a name="notes-for-callers"></a>通話備註
 當使用者請求暫停正在調試的程式時,SDM 將調用[「原因中斷](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)」。。 成功暫停程式後,DE 將傳`IDebugBreakEvent2`送事件 。 此事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="remarks"></a>備註
 例如,用戶可以在 **「調試」** 選單上選擇 **「全部中斷」** 命令,以從運行無限迴圈的程式中斷開。 SDM 通過調用[「原因中斷](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)」告訴程式停止。 當程式最終`IDebugBreakEvent2`停止時,DE 發送。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
