---
title: IDebugApplicationThreadEvents110 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726268"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 介面
新增更多執行緒的事件。 這些事件只是本機。 也就是說，您可以有訂閱只有在處理序正在偵錯，請使用[IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738)通知與取消 PDM 應用程式執行緒物件上的通知方法 (物件實作[IDebugApplicationThread介面](../../winscript/reference/idebugapplicationthread-interface.md))。 都來自在執行緒上發生。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugActivationThreadEvents110` 介面公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|呼叫到使用 PDM 執行緒的執行緒切換已開始。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|執行緒正在從中斷點繼續執行，而且會再次使用中。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|執行緒暫停的中斷點，而且可以處理需要完整暫止執行緒的呼叫。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|呼叫到使用 PDM 執行緒的執行緒切換已完成。|