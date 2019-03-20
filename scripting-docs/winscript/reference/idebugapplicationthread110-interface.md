---
title: IDebugApplicationThread110 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110 Interface
ms.assetid: 25bc351f-3451-4387-9302-078f6292ddff
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a40b1a6f194ef0f335d8c6516b101250b0d980fe
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158405"
---
# <a name="idebugapplicationthread110-interface"></a>IDebugApplicationThread110 介面
提供更多的功能，如[IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)介面。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugApplicationThread110` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationThread110::AsynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread110-asynchronouscallintothread.md)|在主執行緒上進行非同步呼叫。|  
|[IDebugApplicationThread110::GetActiveThreadRequestCount](../../winscript/reference/idebugapplicationthread110-getactivethreadrequestcount.md)|目前正在處理從 PDM 的執行緒切換機制多少執行緒要求的計數。 通常是 0 或 1，但它的可能會更高，如果一個執行緒呼叫開始處理，但觸發程序的執行緒同步呼叫，或否則 （例如，藉由觸發 IDebugApplicationEvents 事件發出偵錯工具暫止的執行緒執行緒）|  
|[IDebugApplicationThread110::IsSuspendedForBreakPoint](../../winscript/reference/idebugapplicationthread110-issuspendedforbreakpoint.md)|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)已在這個執行緒上呼叫，但尚未完成。|  
|[IDebugApplicationThread110::IsThreadCallable](../../winscript/reference/idebugapplicationthread110-isthreadcallable.md)|這個執行緒是處於可以處理使用 PDM 的執行緒切換頻率機制 （例如 SynchronousCallInThread) 進行的呼叫。|