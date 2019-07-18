---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80def3f9c3d270ebd6f2217f6ce39f07ef27b119
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337513"
---
# <a name="idebugfield"></a>IDebugField
這個介面表示的欄位，也就是符號或類型的描述。

## <a name="syntax"></a>語法

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者會實作這個介面的基底類別的所有欄位。

## <a name="notes-for-callers"></a>呼叫端資訊
 這個介面是基底類別的所有欄位。 傳回值為基礎[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)，此介面可能會傳回更具特製化的介面，藉由使用[QueryInterface](/cpp/atl/queryinterface)。 此外，許多介面傳回`IDebugField`從各種方法的物件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugField`。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|取得相關類型的符號可顯示的資訊。|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|取得欄位的類型。|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|取得欄位的型別。|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|取得欄位的容器。|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|取得欄位的位址。|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|取得欄位中，以位元組為單位的大小。|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|取得擴充欄位的相關資訊。|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|比較兩個欄位。|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|取得型別無關的符號或類型資訊。|

## <a name="remarks"></a>備註
 類型相當於 C 語言`typedef`。

 在下列C++語言範例中，`weather`是類別類型，並`sunny`並`stormy`是符號：

```cpp
class weather;
weather sunny;
weather stormy;
```

 欄位代表符號還是類型可決定藉由呼叫[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)檢查[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)結果。 如果`FIELD_KIND_TYPE`設定位元，欄位是一個型別，而且如果`FIELD_KIND_SYMBOL`設定位元，它是一種符號。

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)