---
title: IDebug位址 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f281ceb1f305c5774fedbf725f2e6a9481d073d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736587"
---
# <a name="idebugaddress"></a>IDebugAddress
此介面表示項的位址。 它由符號處理程式返回。

## <a name="syntax"></a>語法

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式實現此介面以表示物件的位址。

## <a name="notes-for-callers"></a>通話備註
 許多介面上的許多方法返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|檢索描述物件及其位置[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構。|

## <a name="remarks"></a>備註
 符號提供程式返回此介面以表示物件及其在特定作用域中的位置(例如,函數、方法或類)。 此介面從符號提供程式和表達式賦值器的各個方法返回並傳遞給。 通常,符號提供程式是唯一需要解釋此介面內容的實體。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
