---
title: IDebug參考2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720271"
---
# <a name="idebugreference2"></a>IDebugReference2
此介面表示對堆疊框架屬性或其他屬性的引用。

> [!NOTE]
> `IDebugReference2`保留以供將來使用,其所有方法應返回`E_NOTIMPL`。

## <a name="syntax"></a>語法

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以表示對特定值類型的引用。 例如,該值可以是表達式計算的結果、用於顯示記憶體的記憶體上下文或寄存器及其值的清單。

## <a name="notes-for-callers"></a>通話備註
 調用[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)以獲取此介面。 [獲取父級](../../../extensibility/debugger/reference/idebugreference2-getparent.md)和[獲取最引用](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)也返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugReference2`。

|方法|描述|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|獲取描述此引用[的DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|從字串設定此引用的值。|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|從另一個引用設定此引用的值。|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|枚舉此引用的子級。|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|獲取此引用的父項。|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|獲取此引用的最派生引用。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|獲取此引用引用的記憶體位元組。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|獲取此引用的記憶體上下文。|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|獲取此引用的大小(以位元組為單位)。|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|設置此引用類型。|
|[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)|將此引用與另一個引用進行比較。|

## <a name="remarks"></a>備註

> [!NOTE]
> 不應將"屬性"的這種使用與類的成員變數的含義混淆,儘管 可以`IDebugReference2`表示此類實體。

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示一個`IDebugReference2`屬性 ,同時表示對屬性的引用,通常是對正在調試的程式中的物件的引用。

 屬性和引用之間的主要區別是屬性引用物件的命名實例,而引用引用未命名的實例。 例如,屬性可以引用程式堆中的物件。 `"a.b"` 另一個屬性可以引用與`"c.d"`的相同物件。 引用此屬性的方式要求`"a.b"`該`"c.d"`或在作用域中。 對同一物件的引用是無名的;只要該物件的記憶體有效,就可以引用該物件。

 可以將`IDebugProperty2`介面視為具有名稱、類型和位址的值。 另`IDebugReference2`一方面,可以認為是類型和位址。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [取得參考](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
