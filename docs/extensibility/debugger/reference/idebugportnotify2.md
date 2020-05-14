---
title: IDebugPortNotify2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724914"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
此介面註冊或取消註冊一個程式,該程式可以使用正在運行的埠進行調試。

## <a name="syntax"></a>語法

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商實現此介面以支援從埠添加和刪除程式。 它通常實現在實現[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面的同一物件上。

## <a name="notes-for-callers"></a>通話備註
 對介面上的[查詢介面](/cpp/atl/queryinterface)的`IDebugPort2`調用將返回此介面。 此外,對[GetPortNotify 的](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)調用將返回此介面。 調試引擎可以將此介面視為[WatchForProvider 事件的](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)參數。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPortNotify2`。

|方法|描述|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|註冊一個程式,該程式可以使用正在運行的埠進行調試。|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|取消註冊可以從正在運行的埠調試的程式。|

## <a name="remarks"></a>備註
 除非調試埠有一種方法來知道何時載入或卸載程式,否則自定義埠供應商必須實現此介面。 使用此介面追蹤載入用於透過特定埠進行調試的所有程式。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
