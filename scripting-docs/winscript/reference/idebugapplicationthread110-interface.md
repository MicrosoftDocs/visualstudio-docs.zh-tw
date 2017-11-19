---
title: "IDebugApplicationThread110 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aee30ae68319810f58bf31f8d0eb32cf8f30d34c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 介面
提供更多的功能，如[IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)介面。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugApplicationThread110` 介面公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|在主執行緒上進行非同步呼叫。|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|目前正在處理從 PDM 執行緒切換機制多少執行緒要求的計數。 通常是 0 或 1，但它的可能為了要能夠更高版本，如果一個執行緒呼叫會開始處理，但觸發出執行緒的同步呼叫，或否則 （例如，透過觸發 IDebugApplicationEvents 事件發出偵錯工具暫止的執行緒執行緒）|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)此執行緒上被呼叫，且尚未完成。|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|這個執行緒是處於可以處理使用 PDM 執行緒切換機制 （例如 SynchronousCallInThread) 進行呼叫的狀態。|