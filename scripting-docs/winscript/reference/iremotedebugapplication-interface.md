---
title: "IRemoteDebugApplication 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea91afdc44b70a91846d7b1a3dc4c017c0c4c80e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication 介面
表示執行的應用程式。 不需要對應到作業系統處理序。 一般而言，偵錯工具為目標的應用程式進行偵錯。 程序進行偵錯管理員通常會實作應用程式物件。  
  
 除了繼承自`IUnknown`、`IRemoteDebugApplication`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|會繼續執行應用程式目前正在中斷點。|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|會在偵錯工具立即中斷應用程式。|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|會在偵錯工具連接到此應用程式。|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|目前的偵錯工具中斷應用程式。|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|傳回目前的偵錯工具連接到應用程式。|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|提供偵錯工具 IDE 中，執行不足的處理序應用程式，在應用程式處理序中建立物件的機制。|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|指出應用程式是否有回應。|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|列舉已知為應用程式相關聯的所有執行緒。|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|傳回這個應用程式節點的名稱。|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|傳回在其下加入應用程式相關聯的所有節點的應用程式節點。|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|列舉執行此應用程式中的所有語言通用的運算式內容。|