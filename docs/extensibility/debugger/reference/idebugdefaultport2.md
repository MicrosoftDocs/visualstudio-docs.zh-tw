---
title: IDebug預設埠2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732310"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
此介面提供了幾種訪問埠伺服器和通知工具的方法。

## <a name="syntax"></a>語法

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 實現此介面以表示用於訪問程式的調試埠。 如果自定義埠供應商處理遠端調試,也可以實現此介面。

## <a name="notes-for-callers"></a>通話備註
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面上的方法的參數提供此介面。 在[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面上調用[查詢介面](/cpp/atl/queryinterface)也可以獲取此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 除了[在 IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)中定義的方法之外,此介面還實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|從此埠獲取埠通知介面。|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|獲取承載此埠的伺服器的介面。|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|確定此埠是否在本地電腦上運行。|

## <a name="remarks"></a>備註
 名稱""`IDebugDefaultPort2`有點用錯,因為它不代表默認埠。 它可以稱為"IDebugPort3"

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
