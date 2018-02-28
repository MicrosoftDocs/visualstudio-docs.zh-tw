---
title: "IActiveScriptSiteDebugEx 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx 介面
實作這個介面，連同`IActiveScriptSiteDebug`介面，如果您要撰寫應用程式中收到執行階段錯誤的通知，並選擇性地將附加至偵錯的應用程式需要的主機。 程序進行偵錯管理員提供透過通知`IActiveScriptDebug`如果只要時間編寫指令碼偵錯工具會在電腦上找到。 如果沒有恰好時間指令碼偵錯工具是找不到，PDM 會提供透過通知`IActiveScriptDebugEx`改為。  
  
 若要取得執行階段錯誤的通知，您的主機必須處理[ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)。 根據使用者的動作，您可以再決定要附加內部偵錯工具和傳回值，還是要傳回的 OnScriptErrorDebug 中偵錯工具啟動`pfEnterDebugger`參數。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|通知主機有關指令碼執行階段錯誤時的處理序偵錯 Manager 找不到外部剛好在時間偵錯工具。|