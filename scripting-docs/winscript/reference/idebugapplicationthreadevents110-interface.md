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
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984399"
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 介面
加入更多執行緒事件。 這些事件僅限本機。 也就是說，您只能在正在進行調試的進程中，使用 PDM 應用程式執行緒物件（執行[IDebugApplicationThread 介面](../../winscript/reference/idebugapplicationthread-interface.md)的物件）上的[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)建議和 unadvise 方法來訂閱它們。 它們會在其來源的執行緒上發生。  
  
> [!IMPORTANT]
> 這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IDebugActivationThreadEvents110` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|已開始使用 PDM 的執行緒切換呼叫執行緒。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|執行緒正在從中斷點繼續，將會再次使用。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|執行緒會暫停中斷點，而且可以處理需要完全暫停執行緒的呼叫。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|使用 PDM 的執行緒切換來呼叫執行緒已完成。|