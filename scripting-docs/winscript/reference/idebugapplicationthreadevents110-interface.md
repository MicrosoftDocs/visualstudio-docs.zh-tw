---
title: IDebugApplicationThreadEvents110 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 0051f18c67fffc9801ad326745a0dc9dd63f4391
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148850"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 介面
新增更多執行緒的事件。 這些事件只是本機。 也就是說，您可以訂閱它們只能在處理序正在偵錯，請使用[IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738)通知與取消方法通知 PDM 應用程式執行緒物件 (物件實作[IDebugApplicationThread介面](../../winscript/reference/idebugapplicationthread-interface.md))。 它們都來自在執行緒上發生。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugActivationThreadEvents110` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|呼叫到使用 PDM 執行緒的執行緒切換已開始。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|執行緒從中斷點繼續執行，並可再次使用。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|執行緒正在暫止中斷點，以及可處理需要完整暫止執行緒的呼叫。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|呼叫到使用 PDM 執行緒的執行緒切換已完成。|