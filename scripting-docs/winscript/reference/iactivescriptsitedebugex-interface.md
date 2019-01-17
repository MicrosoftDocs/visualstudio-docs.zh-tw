---
title: IActiveScriptSiteDebugEx 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e462630f7bf52c4ca94aa59df22616e9a335a7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345873"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx 介面
實作這個介面，連同`IActiveScriptSiteDebug`介面，如果您正在撰寫的主機，必須在應用程式時收到通知的執行階段錯誤，並選擇性地附加至偵錯的應用程式。 處理序偵錯管理員提供通知`IActiveScriptDebug`如果的時間只需編寫指令碼偵錯工具會在電腦上找到。 如果在時間不只要指令碼偵錯工具是找不到，PDM 會提供通知`IActiveScriptDebugEx`改。  
  
 若要取得執行階段錯誤的通知，您的主機必須處理[ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)。 根據使用者動作，您可以再決定是否將傳回時，與內部偵錯工具，或是傳回 OnScriptErrorDebug 中偵錯工具啟動`pfEnterDebugger`參數。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|通知主機有關指令碼執行階段錯誤時的處理序偵錯管理員找不到外部的 「 Just In Time 偵錯工具。|