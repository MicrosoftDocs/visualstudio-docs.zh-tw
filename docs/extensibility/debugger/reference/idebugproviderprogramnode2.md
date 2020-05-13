---
title: IDebug提供程式程序節點2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720676"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
此介面跨進程邊界封送程序相關介面。

## <a name="syntax"></a>語法

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 在實現[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)以支援跨行程邊界封送介面的同一物件上實現此介面。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugProgramNode2`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。 如果無法獲取此介面,DE 不支援介面的封送。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|跨進程邊界獲取指定的介面。|

## <a name="remarks"></a>備註
 當 DE 在獨立於正在除錯的程式的進程空間中執行時,將實現此介面:例如,當 DE 在 Visual Studio 進程空間中執行時,而不是調試程式的進程空間。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
