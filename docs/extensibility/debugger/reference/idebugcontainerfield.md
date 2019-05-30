---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d633b7e42f8c7f64a818539694837b954ea31e72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332520"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
這個介面會表示符號或其他符號或類型的容器型別。

## <a name="syntax"></a>語法

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者所實作的相同物件上實作這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。 此介面也是代表容器的所有介面的基底類別。

## <a name="notes-for-callers"></a>呼叫端資訊
 在許多介面的許多方法會傳回此介面。 因為這是所有容器的基底類別，更具特製化的介面可以從這個介面取得使用[QueryInterface](/cpp/atl/queryinterface)。 這類介面包含[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)， [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)， [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)，以及[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面，這個介面會實作下列方法：

|方法|描述|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|建立容器的欄位的列舉值。|

## <a name="remarks"></a>備註
 陣列 （變數的容器）、 類別 （如方法和變數的容器） 和方法 （在容器中的參數和區域變數） 都是容器的範例。

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)