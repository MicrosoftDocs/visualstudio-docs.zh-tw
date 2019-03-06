---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99b57aece9b835ac1f2277fdd626a9fdff7b903f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705095"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
此介面可讓偵錯管理員 (SDM) 附加至程式，並取得與程式相關聯的 [程式] 節點的工作階段。

## <a name="syntax"></a>語法

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 自訂連接埠供應商的相同物件上實作這個介面[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)為了讓附加至程式時同時允許連接埠提供者，來追蹤所有工作階段連接到 SDM 介面計劃。 自訂連接埠供應商可以實作這個介面，如果選擇。

## <a name="notes-for-callers"></a>呼叫端資訊
 SDM 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugProgram2`介面，以取得這個介面來追蹤已附加至程式的工作階段。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramEx2`。

|方法|描述|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|將程式附加到工作階段。|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|取得與程式相關聯的方案節點。|

## <a name="remarks"></a>備註
 這個介面是 SDM 與程式之間的私用。

## <a name="requirements"></a>需求
 標頭：Portpriv.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)