---
description: 此介面會註冊或取消註冊可使用其執行所在埠進行偵錯工具的程式。
title: IDebugPortNotify2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4000426b72472d57b589f26543dd1547f8dc982
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072386"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
此介面會註冊或取消註冊可使用其執行所在埠進行偵錯工具的程式。

## <a name="syntax"></a>Syntax

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂埠供應商會執行這個介面，以支援從埠新增和移除程式。 它通常會在執行 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 介面的相同物件上執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對介面的 [QueryInterface](/cpp/atl/queryinterface) 呼叫會傳回 `IDebugPort2` 這個介面。 此外，呼叫 [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) 會傳回這個介面。 Debug engine 可以看到這個介面做為 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)的參數。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPortNotify2` 。

|方法|描述|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|註冊可使用其執行所在之埠進行偵錯工具的程式。|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|取消註冊可以從其執行所在之埠進行偵錯工具的程式。|

## <a name="remarks"></a>備註
 除非 debug 埠知道載入或卸載程式的方式，否則自訂埠供應商必須執行此介面。 所有透過特定埠進行偵錯工具的載入程式都會使用這個介面進行追蹤。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
