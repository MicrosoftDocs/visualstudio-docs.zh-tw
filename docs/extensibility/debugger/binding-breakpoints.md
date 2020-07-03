---
title: 系結中斷點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e839b6e0e7967c4802bee5617da3334c5d4033c5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903224"
---
# <a name="bind-breakpoints"></a>系結中斷點
如果使用者設定中斷點（可能是按**F9**），IDE 就會會構成要求並提示 debug 會話建立中斷點。

## <a name="set-a-breakpoint"></a>設定中斷點
 設定中斷點是兩個步驟的程式，因為可能尚未提供受到中斷點影響的程式碼或資料。 首先，必須描述中斷點，然後，當程式碼或資料可供使用時，它必須系結至該程式碼或資料，如下所示：

1. 中斷點是從相關的 debug engine （DEs）要求，然後中斷點會系結至可用的程式碼或資料。

2. 中斷點要求會傳送至 debug 會話，並將它傳送至所有相關的 DEs。 選擇要處理中斷點的任何 DE 都會建立對應的暫止中斷點。

3. Debug 會話會收集暫止的中斷點，並將它們傳回至 debug 封裝（Visual Studio 的偵錯工具元件）。

4. Debug 封裝會提示 debug 會話將暫止的中斷點系結至程式碼或資料。 Debug 會話會將此要求傳送至所有相關的 DEs。

5. 如果 DE 可以系結中斷點，它就會將中斷點系結事件傳回給「debug」會話。 如果不是，它會改為傳送中斷點錯誤事件。

## <a name="pending-breakpoints"></a>暫止中斷點
 暫止的中斷點可以系結至多個程式碼位置。 例如，c + + 範本的源程式碼可以系結至範本所產生的每個程式碼序列。 「偵錯工具」會話可以使用「中斷點系結」事件來列舉傳送事件時系結至中斷點的程式碼內容。 較多的程式碼內容稍後可以系結，因此，DE 可能會針對每個系結要求傳送多個中斷點系結事件。 不過，DE 應該只會針對每個系結要求傳送一個中斷點錯誤事件。

## <a name="implementation"></a>實作
 就程式設計而言，debug 封裝會呼叫會話 debug manager （SDM），並提供[IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面來包裝[BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)結構，其中描述要設定的中斷點。 雖然中斷點可以是許多形式，但它們最終會解析為程式碼或資料內容。

 SDM 會藉由呼叫其[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法，將這個呼叫傳遞給每個相關的 DE。 如果取消選擇要處理中斷點，它會建立並傳回[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。 SDM 會收集這些介面，並將它們當做單一介面傳遞回做為偵錯工具封裝 `IDebugPendingBreakpoint2` 。

 到目前為止，尚未產生任何事件。

 然後，debug 封裝會嘗試藉由呼叫[bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)（由 DE 來執行），將暫止的中斷點系結至程式碼或資料。

 如果中斷點已系結，則 DE 會將[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)事件介面傳送至偵錯工具封裝。 Debug 封裝會使用這個介面，藉由呼叫[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)（傳回一或多個[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面）來列舉系結至中斷點的所有程式碼內容（或單一資料內容）。 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)介面會傳回[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面，而[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)會傳回包含程式碼或資料內容的[BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)聯集。

 如果取消系結無法系結中斷點，則會將單一[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)事件介面傳送至 debug 封裝。 Debug 封裝會藉由呼叫[GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)（後面接著[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)和[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)）來抓取錯誤型別（錯誤或警告）和參考用訊息。 這會傳回包含錯誤類型和訊息的[BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)結構。

 如果取消處理中斷點，但無法系結它，則會傳回類型的錯誤 `BPET_TYPE_ERROR` 。 Debug 封裝會藉由顯示 [錯誤] 對話方塊來回應，而 IDE 會在源程式碼左側的中斷點圖像中放置驚嘆號字元。

 如果 DE 會處理中斷點，則無法系結，但有些其他的可能會將它系結，則會傳回警告。 IDE 會藉由將問題圖像放在源程式碼左側的中斷點圖像中進行回應。

## <a name="see-also"></a>另請參閱
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
