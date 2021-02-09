---
title: IDebugContainerField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e7ed9e573236f0bdeff9c9a8433af322a5a5f79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928493"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
此介面代表做為其他符號或類型之容器的符號或類型。

## <a name="syntax"></a>Syntax

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會在執行 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面的相同物件上，執行這個介面。 這個介面也是表示容器之所有介面的基類。

## <a name="notes-for-callers"></a>呼叫者注意事項
 許多介面上的許多方法會傳回這個介面。 因為這是所有容器的基類，所以可以使用 [QueryInterface](/cpp/atl/queryinterface)從這個介面取得更特製化的介面。 這類介面包括 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)、 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)和 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|建立容器欄位的列舉值。|

## <a name="remarks"></a>備註
 變數) 的陣列 (容器、適用于方法和變數的類別 (容器) 和方法 (容器的參數和區域變數) 為容器的範例。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
