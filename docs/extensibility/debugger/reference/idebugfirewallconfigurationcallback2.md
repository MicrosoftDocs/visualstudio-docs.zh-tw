---
title: IDebug防火牆配置回調2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728720"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
啟用使用 DCOM 要求[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]UI 確保防火牆不會阻止遠端除錯的調試引擎。

## <a name="syntax"></a>語法

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 由會話調試管理器的埠對象實現。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugFirewallConfigurationCallback2`。

|方法|描述|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|請求防火牆不會阻止遠程調試。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll
