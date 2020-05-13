---
title: IDebug程式節點附加2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721828"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
允許通知程式節點嘗試附加到關聯的程式。

## <a name="syntax"></a>語法

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面在實現[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面的同一類上實現,以便接收附加操作的通知並提供取消附加操作的機會。

## <a name="notes-for-callers"></a>通話備註
 通過在`QueryInterface`[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件中調用方法來獲取此介面。 在[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法之前必須調用[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法,以便給程式節點停止附加進程的機會。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|附加到關聯的程式或延遲附加過程到[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。|

## <a name="remarks"></a>備註
 此介面是棄用[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)方法的首選替代方法。 所有調試引擎始終載入函數`CoCreateInstance`,即它們在正在調試的程式的位址空間之外實例化。

 如果`IDebugProgramNode2::Attach_V7`該方法的先前實現只是設置正在調試的`GUID`程式 ,則只需要實現[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。

 如果`IDebugProgramNode2::Attach_V7`該方法的先前實現使用了提供的回調介面,則需要將該功能移動到[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法`IDebugProgramNodeAttach2`的實現, 並且不必實現該介面。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
