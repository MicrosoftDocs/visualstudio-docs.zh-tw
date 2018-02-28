---
title: "IRemoteDebugApplicationEx 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx 介面
表示執行的應用程式。 不需要對應到作業系統處理序。 一般而言，偵錯工具為目標的應用程式進行偵錯。 程序進行偵錯管理員通常會實作應用程式物件。  
  
 除了繼承自`IUnknown`、`IRemoteDebugApplicationEx`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|傳回主應用程式的處理序識別碼。|  
|GetHostMachineName|傳回電腦上執行主應用程式的名稱。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|設定以進行偵錯工具當地語系化的語言。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|會強制進入單一步驟模式偵錯工具。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|撤銷 break 命令。|  
|SetProxyBlanketAndAddRef|更新上偵錯工具的物件 proxy，以確保相容性 Windows 95 型作業系統的遠端偵錯 COM 安全性資訊。|  
|ReleaseFromSetProxyBlanket|從 SetProxyBlanketAndAddRef 版本 AddRef。|