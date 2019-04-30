---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b681b8e6b3ece72144f6b9dd5c18bc7c0b4145
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874003"
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

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll