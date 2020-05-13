---
title: IDebugProgram引擎2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722395"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
程式節點使用此介面來指定可以調試此程式的所有可能的調試引擎 (DE)。

## <a name="syntax"></a>語法

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 或自定義埠供應商在實現[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)的同一物件上實現此介面,以支援建立用於特定程式的特定 DE。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugProgramNode2`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramEngines2`。

|方法|描述|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|指示可以調試此程式的所有可能的 D。|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|選擇要用於除錯此程式的 DE。|

## <a name="remarks"></a>備註
 使用者選擇 DE 後,該選項將調用[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)註冊到程式節點。 選定的引擎成為[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)返回的發動機。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
