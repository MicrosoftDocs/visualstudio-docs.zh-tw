---
title: 繫結中斷點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e1f2e0d1964f742a7dba9ff2dfc7576d86a1a21
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971084"
---
# <a name="bind-breakpoints"></a>繫結中斷點
如果使用者設定中斷點，也許是藉由按下**F9**，IDE 會構成要求，並提示偵錯工作階段，來建立中斷點。  
  
## <a name="set-a-breakpoint"></a>設定中斷點  
 設定中斷點是兩步驟程序，因為程式碼或中斷點受影響的資料可能尚無法使用。 首先，必須描述中斷點，並接著，當程式碼或資料可供使用，它必須繫結至該程式碼或資料，如下所示：  
  
1.  中斷點會從相關的偵錯引擎 (DEs)、 要求，然後中斷點繫結至程式碼或資料可供使用。  
  
2.  中斷點要求會傳送至偵錯工作階段，將它傳送至所有相關的 DEs。 選擇處理中斷點任何 DE 會建立對應的暫止的中斷點。  
  
3.  偵錯工作階段會收集 暫止中斷點，並將其傳送回偵錯套件 （Visual Studio 的偵錯元件）。  
  
4.  偵錯封裝會提示要繫結至程式碼或資料的暫止中斷點的偵錯工作階段。 偵錯工作階段會將此要求傳送至所有相關的 DEs。  
  
5.  如果 DE 就能將中斷點繫結，它會傳送回到偵錯工作階段中斷點繫結的事件。 如果沒有，它會改為傳送中斷點錯誤事件。  
  
## <a name="pending-breakpoints"></a>暫止中斷點  
 暫止中斷點可以繫結到多個程式碼位置。 例如，c + + 範本的原始程式碼行可以繫結至從範本產生每個程式碼序列。 偵錯工作階段可以使用中斷點繫結的事件，來列舉在傳送事件的時間繫結至中斷點的程式碼內容。 更新版本中，可以繫結更多的程式碼內容，因此 DE 可能會傳送多個中斷點繫結的每個繫結要求的事件。 不過，DE 應該傳送每個繫結要求的只有一個中斷點錯誤事件。  
  
## <a name="implementation"></a>實作  
 以程式設計的方式，會呼叫偵錯工作階段管理員 (SDM) 偵錯封裝，並為其提供[IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)包裝的介面[BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)結構描述若要設定的中斷點。 中斷點可以是許多形式，雖然它們最終會解析成的程式碼或資料內容。  
  
 SDM 會將每個相關的 DE 此呼叫傳遞藉由呼叫其[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法。 如果 DE 選擇處理中斷點，它會建立並傳回[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。 在 SDM 會收集這些介面，並將其傳遞回偵錯封裝成單一`IDebugPendingBreakpoint2`介面。  
  
 到目前為止，已不產生任何事件。  
  
 偵錯套件然後嘗試將暫止中斷點繫結至程式碼或資料藉由呼叫[繫結](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)，這藉由德國。  
  
 如果中斷點已繫結，就會傳送 DE [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)偵錯封裝的事件介面。 藉由呼叫這個介面來列舉所有的程式碼內容 （或單一資料內容） 繫結至中斷點的偵錯封裝用法[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)，它會傳回一或多個[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。 [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)介面傳回[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面，並[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)傳回[BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)包含的程式碼或資料內容的聯集。  
  
 如果無法繫結中斷點 DE，它會傳送單一[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)偵錯封裝的事件介面。 偵錯封裝擷取的錯誤類型 （錯誤或警告） 和參考用訊息藉由呼叫[GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)，後面接著[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)和[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)。 這會傳回[BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)結構，其中包含的錯誤類型和訊息。  
  
 如果 DE 處理中斷點，但無法加以繫結，它會傳回型別的錯誤`BPET_TYPE_ERROR`。 偵錯封裝會顯示錯誤對話方塊，以回應，IDE 會放在左邊的原始程式碼行中斷點字符的驚嘆號圖像 （glyph）。  
  
 如果 DE 處理中斷點，但無法繫結，但是其他 DE 可能會將它繫結，它會傳回一則警告。 IDE 會回應將放在左邊的原始程式碼行的中斷點圖像 （glyph） 的問題圖像 （glyph）。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)