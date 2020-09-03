---
title: IDebugProgramEngines2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722395"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
程式節點會使用此介面來指定所有可能的偵錯工具引擎 (DE) 可將此程式進行偵錯工具。

## <a name="syntax"></a>語法

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 取消或自訂埠供應商會在執行 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 的相同物件上，執行此介面，以支援建立特定程式所要使用的特定取消。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProgramEngines2` 。

|方法|描述|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|指出可以對此程式進行偵錯工具的所有可能 DEs。|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|選取要用來對此程式進行偵錯工具的取消。|

## <a name="remarks"></a>備註
 一旦使用者選擇取消，該選項就會藉由呼叫 [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)向程式節點註冊。 選取的引擎會成為 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)所傳回的引擎。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
