---
title: IDebug消息事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727369"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
除錯引擎 (DE) 使用此介面向 Visual Studio 發送消息,該訊息需要用戶回應。

## <a name="syntax"></a>語法

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以向需要使用者回應的 Visual Studio 發送消息。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。

 此介面的實現必須將 Visual Studio 的[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)調用傳達給 DE。 例如,這可以通過發佈到 DE 的消息處理線程的消息來完成,或者實現此介面的物件可以保留對 DE 的引用,`IDebugMessageEvent2::SetResponse`並在將回應傳遞到 下調用 DE。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以向需要回應的用戶顯示消息。 該事件使用 SDM 在附加到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugMessageEvent2`。

|方法|描述|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|獲取要顯示的消息。|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|從消息框中設置回應(如果有)。|

## <a name="remarks"></a>備註
 如果 DE 需要使用者對特定消息的特定回應,則 DE 將使用此介面。 例如,如果 DE 在嘗試遠端附加到程式後收到「訪問被拒絕」訊息,則 DE 在具有`IDebugMessageEvent2``MB_RETRYCANCEL`消息框樣式的事件中將此特定消息發送到 Visual Studio。 這允許用戶重試或取消附加操作。

 DE 指定如何按照 Win32`MessageBox`函數 的約定處理此消息(有關詳細資訊,請參閱[AfxMessageBox)。](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

 使用[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)介面向不需要使用者回應的 Visual Studio 發送消息。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
