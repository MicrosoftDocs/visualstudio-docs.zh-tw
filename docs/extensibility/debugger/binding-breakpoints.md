---
title: 綁定斷點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739227"
---
# <a name="bind-breakpoints"></a>繫結斷點
如果用戶設置斷點(可能通過按**F9),IDE**將制定請求並提示調試會話創建斷點。

## <a name="set-a-breakpoint"></a>設定中斷點
 設置斷點是一個兩步過程,因為受斷點影響的代碼或數據可能尚未可用。 首先,必須描述斷點,然後,當代碼或數據可用時,必須將其綁定到該代碼或數據,如下所示:

1. 從相關調試引擎 (DEs) 請求斷點,然後斷點在可用時綁定到代碼或數據。

2. 斷點請求發送到調試會話,調試會話將其發送到所有相關的 D。 任何選擇處理斷點的 DE 都會創建相應的掛起斷點。

3. 除錯工作階段收集掛起的斷點並將其發送回調試包(Visual Studio 的調試元件)。

4. 調試包提示調試會話將掛起的斷點綁定到代碼或數據。 除錯工作階段將此請求發送到所有相關的 D。

5. 如果 DE 能夠綁定斷點,它將一個斷點綁定事件發送回調試會話。 如果沒有,它將發送斷點錯誤事件。

## <a name="pending-breakpoints"></a>暫停的斷點
 掛起的斷點可以綁定到多個代碼位置。 例如,C++範本的一行原始碼可以綁定到從範本生成的每個代碼序列。 除錯工作階段可以使用斷點綁定事件枚舉在發送事件時綁定到斷點的代碼上下文。 以後可以綁定更多程式碼上下文,因此 DE 可能會為每個綁定請求發送多個斷點綁定事件。 但是,DE 應僅發送每個綁定請求的一個斷點錯誤事件。

## <a name="implementation"></a>實作
 在程式設計上,調試包調用會話調試管理器 (SDM),並給它一個[IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面,該介面包裝[BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md)結構,該結構描述了要設置的斷點。 儘管斷點可以是多種形式,但它們最終解析為代碼或數據上下文。

 SDM 通過調用其[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法將此調用傳遞給每個相關的 DE。 如果 DE 選擇處理斷點,它將創建並返回[IDebug PendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。 SDM 收集這些介面並將其作為單`IDebugPendingBreakpoint2`個 介面傳回調試包。

 到目前為止,尚未生成任何事件。

 然後,調試包嘗試通過調用 DE 實現的[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)將掛起的斷點綁定到代碼或數據。

 如果斷點綁定,DE 會向調試包發送[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)事件介面。 除錯套件使用此介面透過呼叫[EnumBoundBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)來枚舉綁定到斷點的的所有程式碼上下文(或單個資料上下文),該介面返回一個或多個[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。 [GetBreakpoint 解析](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)介面傳回[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面[,GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)返回包含代碼或數據上下文[BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)聯合。

 如果 DE 無法綁定斷點,它將向調試包發送單個[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)事件介面。 除錯套件透過除錯[的 GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)的檢查錯誤類型(錯誤或警告)與資訊性訊息,然後是[GetBreakpoint 解析](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)與[Get解析資訊](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)。 這將返回包含錯誤類型和消息[BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)結構。

 如果 DE 處理斷點但無法結合, 它會傳回`BPET_TYPE_ERROR`型態錯誤 。 調試包通過顯示錯誤對話框進行回應,IDE 在原始程式碼列左側的斷點字形內放置一個感嘆號。

 如果 DE 處理斷點,無法綁定它,但其他 DE 可能會綁定它,則返回警告。 IDE 通過在原始程式碼列左側的斷點字形內放置一個問題字形來回應。

## <a name="see-also"></a>另請參閱
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
