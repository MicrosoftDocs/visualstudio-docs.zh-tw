---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b2aa5c4e45dbdf126a0144ebdfd9a0b102e170
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010281"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
可讓要求則會使用 DCOM 的偵錯引擎[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI，請確定防火牆會封鎖遠端偵錯。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 實作工作階段的偵錯管理員的連接埠物件。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugFirewallConfigurationCallback2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|防火牆未封鎖遠端偵錯的要求。|  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll