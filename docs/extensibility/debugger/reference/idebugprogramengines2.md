---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a5ad34904a2f0bf02e5a2221f1ff73093012a41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916926"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
程式節點會使用此介面來指定所有可能的偵錯引擎 (DE) 可以偵錯此程式。

## <a name="syntax"></a>語法

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 或自訂的連接埠提供者會實作這個介面上相同的物件會實作[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)來支援建立特定的規定，若要使用特定程式。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugProgramNode2`介面，以取得此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramEngines2`。

|方法|描述|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|指出可以進行偵錯此程式的所有可能 DEs。|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|選取要用於偵錯此程式 DE。|

## <a name="remarks"></a>備註
 由使用者選擇規定之後, 程式節點註冊該選擇藉由呼叫[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)。 選取的引擎會變成所傳回的引擎[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)