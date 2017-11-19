---
title: "IDebugFirewallConfigurationCallback2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab632bc7db06f01c6a88070a065c6939e4dbb91f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
可讓偵錯引擎，使用 DCOM 詢問[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI，請確定防火牆會封鎖遠端偵錯。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 藉由偵錯工作階段管理員的連接埠物件。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugFirewallConfigurationCallback2`。  
  
|方法|說明|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|確認防火牆不會封鎖遠端偵錯要求。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll