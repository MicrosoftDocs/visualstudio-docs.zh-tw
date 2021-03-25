---
description: 啟用可使用 DCOM 要求 Visual Studio UI 的偵錯工具，以確保防火牆不會封鎖遠端偵錯程式。
title: IDebugFirewallConfigurationCallback2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c67cc1ab9335cfeb197ca67937510b3137d6432c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073608"
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
