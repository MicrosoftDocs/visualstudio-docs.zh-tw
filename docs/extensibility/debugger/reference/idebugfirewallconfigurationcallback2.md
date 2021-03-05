---
description: 啟用使用 DCOM 的偵測引擎來要求 Visual Studio UI，以確保防火牆不會封鎖遠端偵錯程式。
title: IDebugFirewallConfigurationCallback2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf8659a1bc4af55a9809a3c85548b971a7193b26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166524"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
啟用使用 DCOM 的偵錯工具引擎，以要求 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI 確定防火牆不會封鎖遠端偵錯程式。

## <a name="syntax"></a>Syntax

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 由會話 debug manager 的 port 物件所執行。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugFirewallConfigurationCallback2` 。

|方法|描述|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|要求防火牆不會封鎖遠端偵錯程式。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll
