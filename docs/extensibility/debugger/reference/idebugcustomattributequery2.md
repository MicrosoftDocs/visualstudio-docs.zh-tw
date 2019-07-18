---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00220574ac9c16bdab9abd64adde1877ee0fd9f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335809"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
判斷此欄位的自訂屬性存在，如果存在的話，會傳回屬性資訊。

## <a name="syntax"></a>語法

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者所實作的相同物件上實作這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)以支援自訂屬性。

## <a name="notes-for-callers"></a>呼叫端資訊
 使用[QueryInterface](/cpp/atl/queryinterface)若要取得從這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法**IDebugCustomAttributeQuery**介面。

|方法|描述|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|判斷名稱是否存在的自訂屬性。|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|取得指定的自訂屬性的屬性資訊。|

 除了**IDebugCustomAttributeQuery**方法，`IDebugCustomAttributeQuery2`實作下列方法：

|方法|描述|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|取得附加至這個欄位的所有自訂屬性的列舉值。|

## <a name="remarks"></a>備註
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)方法可以傳回為這個欄位定義的所有自訂屬性的列舉值。

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)