---
title: 系結中斷點 |Microsoft Docs
description: 瞭解 IDE 如何會構成中斷點的要求，並在使用者設定中斷點時提示 debug 會話建立中斷點。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 606c1f4cb5559722028b78ef4ef21c41c0ba5556
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914708"
---
# <a name="bind-breakpoints"></a>系結中斷點
如果使用者設定中斷點（也許是按 **F9**），IDE 就會會構成要求，並提示 debug 會話來建立中斷點。

## <a name="set-a-breakpoint"></a>設定中斷點
 設定中斷點是兩個步驟的進程，因為可能還無法使用中斷點所影響的程式碼或資料。 首先，必須描述中斷點，然後當程式碼或資料變成可用時，它必須系結至該程式碼或資料，如下所示：

1. 中斷點是從相關的偵錯工具引擎要求 (DEs) ，然後中斷點會在程式碼或資料變成可用時加以系結。

2. 中斷點要求會傳送至 debug 會話，以將其傳送至所有相關的 DEs。 選擇要處理中斷點的任何 DE 都會建立對應的暫止中斷點。

3. Debug 會話會收集暫止的中斷點，並將其傳送回 debug 封裝， (Visual Studio) 的偵錯工具元件。

4. Debug 封裝會提示 debug 會話將暫止中斷點系結至程式碼或資料。 Debug 會話會將此要求傳送給所有相關的 DEs。

5. 如果 DE 可以系結中斷點，則會將中斷點系結事件傳送回 debug 會話。 如果沒有，則會改為傳送中斷點錯誤事件。

## <a name="pending-breakpoints"></a>暫止中斷點
 暫止中斷點可以系結至多個程式碼位置。 例如，c + + 範本的源程式碼可以系結至從範本產生的每個程式碼順序。 在傳送事件時，debug 會話可以使用中斷點系結事件來列舉系結至中斷點的程式碼內容。 稍後可以系結更多程式碼內容，因此 DE 可能會針對每個系結要求傳送多個中斷點系結事件。 不過，每個系結要求都只會傳送一個中斷點錯誤事件。

## <a name="implementation"></a>實作
 Debug 封裝會以程式設計的方式呼叫 (SDM) 的會話 debug manager，並為它提供包裝[BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)結構的[IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面，其中描述要設定的中斷點。 雖然中斷點可以是許多形式，但它們最終會解析為程式碼或資料內容。

 SDM 會呼叫其 [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 方法，將此呼叫傳遞給每個相關的 DE。 如果取消選擇處理中斷點，則會建立並傳回 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 介面。 SDM 會收集這些介面，並將它們以單一介面的形式傳遞回 debug 封裝中 `IDebugPendingBreakpoint2` 。

 到目前為止，尚未產生任何事件。

 然後，debug 封裝會藉由呼叫 [bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)來嘗試將暫止中斷點系結至程式碼或資料，此系結是由 DE 所執行。

 如果中斷點已系結，則會將 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 事件介面傳送至 debug 封裝。 Debug 封裝會使用這個介面，藉由呼叫 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)（傳回一或多個 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 介面）來列舉系結至中斷點的所有程式碼內容 (或單一資料內容) 。 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)介面會傳回[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面，而[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)會傳回包含程式碼或資料內容[BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)聯集。

 如果 DE 無法系結中斷點，則會將單一 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 事件介面傳送至 debug 封裝。 Debug 封裝會藉由呼叫 [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)，並接著 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) 和 [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)，來抓取錯誤類型 (錯誤或警告) 和參考訊息。 這會傳回包含錯誤類型和訊息的 [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) 結構。

 如果 DE 處理中斷點但無法系結，它會傳回類型的錯誤 `BPET_TYPE_ERROR` 。 偵錯工具封裝會藉由顯示 [錯誤] 對話方塊來回應，IDE 會在源程式碼左邊的中斷點字元內放置驚嘆號符號。

 如果 DE 處理中斷點，則無法將它系結，但有些其他的 DE 可能會系結，它會傳回警告。 IDE 會在源程式碼左邊的中斷點字元內放置問題圖像來回應。

## <a name="see-also"></a>另請參閱
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
