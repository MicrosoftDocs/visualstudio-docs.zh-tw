---
title: IDebugField |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728748"
---
# <a name="idebugfield"></a>IDebugField
此介面表示一個字段,即符號或類型的說明。

## <a name="syntax"></a>語法

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式實現此介面作為所有欄位的基類。

## <a name="notes-for-callers"></a>通話備註
 此介面是所有欄位的基類。 基於[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)的傳回值,此介面可以使用查詢介面傳回更專用[的介面](/cpp/atl/queryinterface)。 此外,許多介面返回來自`IDebugField`各種方法的物件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugField`。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|獲取有關符號或類型的可顯示資訊。|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|獲取欄位的種類。|
|[取得類型](../../../extensibility/debugger/reference/idebugfield-gettype.md)|獲取欄位的類型。|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|獲取欄位的容器。|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|獲取欄位的位址。|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|獲取欄位的大小(以位元組為單位)。|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|獲取有關欄位的擴展資訊。|
|[等於](../../../extensibility/debugger/reference/idebugfield-equal.md)|比較兩個字段。|
|[取得類型資訊](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|獲取有關符號或類型的類型無關的資訊。|

## <a name="remarks"></a>備註
 型態等效於`typedef`C 語言 。

 在以下C++語言範例中,`weather`是類類型,`sunny``stormy`並且是符號:

```cpp
class weather;
weather sunny;
weather stormy;
```

 欄位是否表示符號或類型可以通過調用[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)並檢查[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)結果來確定。 如果設置了`FIELD_KIND_TYPE`位,則欄位為類型,`FIELD_KIND_SYMBOL`如果位已設置,則該欄位為符號。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
