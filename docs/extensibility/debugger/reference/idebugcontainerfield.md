---
title: IDebug容器欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733211"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
此介面表示符號或類型,該符號或類型是其他符號或類型的容器。

## <a name="syntax"></a>語法

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面的同一對象上實現此介面。 此介面也是表示容器的所有介面的基類。

## <a name="notes-for-callers"></a>通話備註
 許多介面上的許多方法返回此介面。 由於這是所有容器的基類,因此可以使用[QueryInterface](/cpp/atl/queryinterface)從該介面獲取更專用的介面。 此類介面包括 IDebugarrayField、IDebugClassfield、IDebugMethodfield 和[IDebugPropertyfield。](../../../extensibility/debugger/reference/idebugpropertyfield.md) [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|為容器的欄位創建枚舉器。|

## <a name="remarks"></a>備註
 陣列(變數的容器)、類(方法和變數的容器)和方法(參數和局部變數的容器)都是容器的示例。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
