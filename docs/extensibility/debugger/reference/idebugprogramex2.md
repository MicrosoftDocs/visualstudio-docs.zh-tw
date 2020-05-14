---
title: IDebugProgramEx2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722326"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
此介面允許工作階段除錯管理員 (SDM) 附加到程式,並獲取程式節點與程式關聯。

## <a name="syntax"></a>語法

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商在[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的同一物件上實現此介面,以便允許 SDM 附加到程式,同時允許埠供應商跟蹤附加到程式的所有作業階段。 如果選擇,自定義埠供應商可以實現此介面。

## <a name="notes-for-callers"></a>通話備註
 SDM`IDebugProgram2`在介面上調用[QueryInterface](/cpp/atl/queryinterface)以獲取此介面以追蹤已附加到程式的作業階段。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramEx2`。

|方法|描述|
|------------|-----------------|
|[附加](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|將程式附加到會話。|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|獲取與程式關聯的程序節點。|

## <a name="remarks"></a>備註
 此介面在 SDM 和程序之間是私有的。

## <a name="requirements"></a>需求
 標題: 波特普里夫.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
