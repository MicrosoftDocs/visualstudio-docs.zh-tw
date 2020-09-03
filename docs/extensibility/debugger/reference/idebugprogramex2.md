---
title: IDebugProgramEx2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722326"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
此介面可讓會話 debug manager (SDM) 附加至程式，並取得與程式相關聯的程式節點。

## <a name="syntax"></a>語法

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂通訊埠供應商會在與 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面相同的物件上執行這個介面，以便讓 SDM 附加至程式，同時允許埠供應商追蹤附加至程式的所有會話。 自訂埠供應商可以在選擇的情況下，執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 SDM 會呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` 來取得這個介面，以追蹤已附加至程式的會話。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProgramEx2` 。

|方法|描述|
|------------|-----------------|
|[附加](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|將程式附加至會話。|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|取得與程式相關聯的程式節點。|

## <a name="remarks"></a>備註
 這個介面在 SDM 和程式之間是私用的。

## <a name="requirements"></a>需求
 標頭： Portpriv。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
