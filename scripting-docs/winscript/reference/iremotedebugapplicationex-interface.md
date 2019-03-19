---
title: IRemoteDebugApplicationEx 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9e25a28ade1ac73b9e4837dae61e2d91f24c45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144403"
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx 介面
代表執行中應用程式。 它不需要對應至作業系統處理序。 一般而言，偵錯工具的目標應用程式進行偵錯。 處理序偵錯管理員通常會實作應用程式物件。  
  
 除了繼承自方法`IUnknown`，則`IRemoteDebugApplicationEx`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|傳回主應用程式的處理序識別碼。|  
|GetHostMachineName|傳回主應用程式執行所在電腦的名稱。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|設定偵錯工具當地語系化的語言。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|會強制進入單一步驟模式偵錯工具。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|撤銷 break 命令。|  
|SetProxyBlanketAndAddRef|更新以確保相容性 Windows 95 型作業系統的遠端偵錯的偵錯工具物件的 proxy 上的 COM 安全性資訊。|  
|ReleaseFromSetProxyBlanket|從 SetProxyBlanketAndAddRef 版本 AddRef。|