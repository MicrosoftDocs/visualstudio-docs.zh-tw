---
description: 程式節點會使用此介面來指定所有可能的偵錯工具引擎 (DE) 可將此程式進行偵錯工具。
title: IDebugProgramEngines2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c19b4dc3967cf7001144d38114a1f873776cb2b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149583"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
程式節點會使用此介面來指定所有可能的偵錯工具引擎 (DE) 可將此程式進行偵錯工具。

## <a name="syntax"></a>Syntax

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

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
