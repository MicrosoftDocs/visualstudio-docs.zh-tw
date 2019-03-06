---
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2427bfbc70c992cfcd41217aec56aa94d825faae
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713421"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
這個介面會註冊，或取消註冊使用其執行的連接埠可以進行偵錯的程式。

## <a name="syntax"></a>語法

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 自訂的連接埠提供者會實作這個介面，以支援新增和移除連接埠的程式。 它通常會實作相同的物件會實作[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugPort2`介面會傳回此介面。 此外，呼叫[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)傳回此介面。 偵錯引擎可以看到此介面做為參數[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPortNotify2`。

|方法|描述|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|可以進行偵錯的程式會向其執行的連接埠。|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|取消註冊才能進行偵錯連接埠上執行的程式。|

## <a name="remarks"></a>備註
 除非偵錯連接埠有辦法知道程式會載入或卸載時，自訂的連接埠提供者必須實作這個介面。 使用此介面，來追蹤已載入偵錯透過特定的連接埠的所有程式。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)