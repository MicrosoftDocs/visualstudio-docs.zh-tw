---
description: 此介面描述埠。
title: IDebugPortRequest2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ca2d1d59c66c87c2dbb0fc256481d35ad590dbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142618"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
此介面描述埠。 此描述可用來將埠新增至埠供應商。

## <a name="syntax"></a>Syntax

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Visual Studio 通常會在從埠供應商取得 debug 埠的過程中，執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 此介面會傳遞至 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 以建立 debug 埠。 對 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) 的呼叫會傳回這個介面，代表用來在第一個位置建立埠的要求。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPortRequest2` 。

|方法|描述|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|取得要建立之埠的名稱。|

## <a name="remarks"></a>備註
 Debug engine 通常不會與埠供應商互動，而且不會使用此介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
