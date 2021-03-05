---
description: 此介面提供數種存取埠伺服器和通知設備的方法。
title: IDebugDefaultPort2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5ec637daa197574710978af7cb22195c969f48b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154414"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
此介面提供數種存取埠伺服器和通知設備的方法。

## <a name="syntax"></a>Syntax

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Visual Studio 會執行這個介面，以代表用於存取程式的 debug 埠。 如果自訂埠供應商處理遠端偵錯，也可以執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面上方法的引數會提供這個介面。 在[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面上呼叫[QueryInterface](/cpp/atl/queryinterface)也可以取得這個介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 除了 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)中定義的方法之外，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|從這個埠取得埠通知介面。|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|取得裝載此埠之伺服器的介面。|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|判斷此埠是否正在本機電腦上執行。|

## <a name="remarks"></a>備註
 名稱 " `IDebugDefaultPort2` " 有點 misnomer，因為它不代表預設埠。 它可能稱為「IDebugPort3」。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
