---
title: IDebugPointerfield |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725603"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
此介面表示指標類型。

## <a name="syntax"></a>語法

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式實現此介面以表示指標。

## <a name="notes-for-callers"></a>通話備註
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_POINTER`,請使用[查詢介面](/cpp/atl/queryinterface)從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 除了`IDebugField``IDebugContainerField`和介面上的方法之外,此介面還實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|返回描述指標目標的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md)|

## <a name="remarks"></a>備註
 在 C/C++ 中,如果指標與陣列表示法一起使用,則可以是容器。 例如,給定`char *pString``pString`的具有`char`指向的指標類型。 `pString[3]`具有容器的類型,該容器是引用`char`該容器的第四個元素的指標。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
