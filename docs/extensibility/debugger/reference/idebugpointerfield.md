---
title: IDebugPointerField |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725603"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
這個介面代表指標類型。

## <a name="syntax"></a>語法

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會執行這個介面來表示指標。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回，請使用[QueryInterface](/cpp/atl/queryinterface)從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面取得這個介面 `FIELD_TYPE_POINTER` 。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 除了和介面上的方法 `IDebugField` `IDebugContainerField` ，這個介面會實作為下列方法：

|方法|描述|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|傳回描述指標目標的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。|

## <a name="remarks"></a>備註
 在 C/c + + 中，指標可以是搭配陣列標記法使用的容器。 例如，假設 `char *pString` `pString` 有一種指標類型 `char` 。 `pString[3]` 具有容器的型別，其為 `char` 參考該容器之第四個元素的指標。

## <a name="requirements"></a>需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
