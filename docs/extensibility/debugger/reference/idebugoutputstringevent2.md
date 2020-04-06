---
title: IDebug輸出Stringevent2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726027"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
此介面由除錯引擎 (DE) 傳送到工作階段除錯管理員 (SDM) 以輸出字串。

## <a name="syntax"></a>語法

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以將字串發送到 IDE 的**輸出**視窗。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以將字串發送到**輸出**視窗。 該事件使用 SDM 在附加到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugOutputStringEvent2`。

|方法|描述|
|------------|-----------------|
|[取得String](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|獲取可顯示的消息。|

## <a name="remarks"></a>備註
 例如,在非託管代碼中,當正在調試的程式向 Win32`OutputDebugString`函數發送字串時,要輸出的字串可以產生。 此字串被 DE 截獲,並`IDebugOutputStringEvent2`作為 事件發送到 SDM。

 使用[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)發送需要用戶回應的消息。

 使用[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)發送不需要回應的錯誤訊息。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
