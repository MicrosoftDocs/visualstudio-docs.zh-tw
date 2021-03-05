---
description: 允許程式節點在嘗試附加至相關聯的程式時收到通知。
title: IDebugProgramNodeAttach2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa623097224afc4f3a6b93d6b98ece0e14149ca5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171730"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
允許程式節點在嘗試附加至相關聯的程式時收到通知。

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面會在實 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 介面的相同類別上執行，以便接收附加作業的通知，以及提供取消附加作業的機會。

## <a name="notes-for-callers"></a>呼叫者注意事項
 藉由呼叫 `QueryInterface` [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件中的方法來取得這個介面。 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法必須在[attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法之前呼叫，才能讓程式節點有機會停止附加進程。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|附加至相關聯的程式，或將附加進程延後至 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。|

## <a name="remarks"></a>備註
 這個介面是被取代之 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) 方法的慣用替代方法。 所有的偵錯工具引擎一律會與函式一起載入 `CoCreateInstance` ，也就是說，它們會在要進行偵錯工具的位址空間之外進行具現化。

 如果先前的方法實值 `IDebugProgramNode2::Attach_V7` 只是設定 `GUID` 要進行偵錯工具的，則只需要執行 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。

 如果先前的 `IDebugProgramNode2::Attach_V7` 方法執行使用提供的回呼介面，則該功能必須移至 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法的執行，而 `IDebugProgramNodeAttach2` 不需要執行介面。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
