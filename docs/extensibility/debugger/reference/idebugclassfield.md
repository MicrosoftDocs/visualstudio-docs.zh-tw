---
title: IDebugClassfield |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734297"
---
# <a name="idebugclassfield"></a>IDebugClassField
此介面將類表示為類型。

## <a name="syntax"></a>語法

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面的同一對象上實現此介面。 此介面是表示類類型的專門化。

## <a name="notes-for-callers"></a>通話備註
 許多介面都有可以返回此介面的方法,包括[IDebugSymbolProvider、IDebugMethodField](../../../extensibility/debugger/reference/idebugsymbolprovider.md)和[IDebugCustom 屬性](../../../extensibility/debugger/reference/idebugcustomattribute.md)。 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 此外,如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法`FIELD_TYPE_CLASS`返回標誌 ,則可以使用[QueryInterface](/cpp/atl/queryinterface)從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面上的方法外,此介面還實現了以下功能:

|方法|描述|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|為此類的基類創建枚舉器。|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|確定是否在類中定義了特定介面。|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|為此類的嵌套類創建枚舉器。|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|獲取包含此類的類。|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|為此類實現的介面創建枚舉器。|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|為此類的構造函數創建枚舉器。|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|獲取預設索引器的名稱。|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|為此類的嵌套枚舉器創建枚舉器。|

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
