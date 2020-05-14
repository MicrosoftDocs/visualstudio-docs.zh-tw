---
title: IDebugarrayfield |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736300"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
此介面描述陣列符號或類型。

## <a name="syntax"></a>語法

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面的同一對象上實現此介面。 此介面是表示陣組物件的專門化。

## <a name="notes-for-callers"></a>通話備註
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_TYPE_ARRAY`返回標誌 ,則使用[查詢介面](/cpp/atl/queryinterface)從[IDebug 容器欄位](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面上的方法外,此介面還實現了以下功能:

|方法|描述|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|取得陣列中的項目數。|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|獲取陣列中的元素類型。|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|獲取陣列的排名。|

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
