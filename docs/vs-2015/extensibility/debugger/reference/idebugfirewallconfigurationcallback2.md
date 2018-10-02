---
title: IDebugFirewallConfigurationCallback2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8d332b7dab143b1fedbbdfc5ac92dc2b123dfe1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498234"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugFirewallConfigurationCallback2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfirewallconfigurationcallback2)。  
  
可讓要求則會使用 DCOM 的偵錯引擎[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]UI，請確定防火牆會封鎖遠端偵錯。  
  
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
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

