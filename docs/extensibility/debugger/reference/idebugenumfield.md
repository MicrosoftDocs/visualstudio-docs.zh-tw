---
title: IDebugenumfield |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7885f36a113809e81279498a769e257af4f1cde2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730165"
---
# <a name="idebugenumfield"></a>IDebugEnumField
此介面表示枚舉類型。

## <a name="syntax"></a>語法

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式實現此介面以表示枚舉。

## <a name="notes-for-callers"></a>通話備註
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_ENUM`,請使用[查詢介面](/cpp/atl/queryinterface)從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依 VTable 順序排列的方法
 除了`IDebugField``IDebugContainerField`和介面上的方法之外,此介面還實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|返回描述此枚舉類型名稱的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md)|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|返回與給定值關聯的枚舉常量的名稱。|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|傳回與給定枚舉常量名稱關聯的值|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|返回與給定枚舉常量名稱關聯的值,但忽略大小寫。|

## <a name="remarks"></a>備註
 它是實際綁定到具有[綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)的位置的基礎符號。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
