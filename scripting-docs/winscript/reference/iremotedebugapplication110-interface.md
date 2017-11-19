---
title: "IRemoteDebugApplication110 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplication110 Interface
ms.assetid: 785ab46a-8827-41cb-806a-132e6b2c8f47
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d384cea22b79b2a7ca9af3424d053fb3062d79a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110-interface"></a>IRemoteDebugApplication110 介面
用來提供新功能，指令碼偵錯工具可以呼叫同處理序的呼叫端。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IRemoteDebugApplication110` 介面公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IRemoteDebugApplication110::SetDebuggerOptions](../../winscript/reference/iremotedebugapplication110-setdebuggeroptions.md)|呼叫以更新偵錯工具選項。 選項預設值為 0 (SDO_NONE)。|  
|[IRemoteDebugApplication110::GetCurrentDebuggerOptions](../../winscript/reference/iremotedebugapplication110-getcurrentdebuggeroptions.md)|傳回目前的資料集的啟用選項。|  
|[IRemoteDebugApplication110::GetMainThread](../../winscript/reference/iremotedebugapplication110-getmainthread.md)|傳回主執行緒呼叫 SetSite 的主機。|