---
title: IDebugReference2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3f1ae87cc9d0926d7afc22d819dddf672a89afd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883801"
---
# <a name="idebugreference2"></a>IDebugReference2
這個介面代表堆疊框架屬性或其他屬性的參考。

> [!NOTE]
> `IDebugReference2` 保留供日後使用，且其所有方法都應傳回 `E_NOTIMPL` 。

## <a name="syntax"></a>Syntax

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以代表特定類型值的參考。 例如，值可能是運算式評估的結果、用來顯示記憶體的記憶體內容，或是暫存器清單及其值的數值。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) 以取得這個介面。 [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) 和 [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) 也會傳回這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugReference2` 。

|方法|描述|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|取得描述此參考的 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構。|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|從字串設定這個參考的值。|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|從另一個參考設定此參考的值。|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|列舉此參考的子系。|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|取得此參考的父系。|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|取得此參考的最高衍生參考。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|取得此參考所參考的記憶體位元組。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|取得此參考的記憶體內容。|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|取得此參考的大小（以位元組為單位）。|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|設定此參考型別。|
|[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)|比較這個參考與另一個。|

## <a name="remarks"></a>備註

> [!NOTE]
> 雖然可以表示這類實體，但不應該將「屬性」的用法與表示類別的成員變數混淆 `IDebugReference2` 。

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 代表屬性（property），而 `IDebugReference2` 代表屬性（property）的參考，通常是所要進行的程式設計程式中物件的參考。

 屬性和參考之間的主要差異在於，屬性會參考物件的已命名實例，而參考則是參考未命名的實例。 例如，屬性可能會參考程式堆積中的物件 `"a.b"` 。 另一個屬性可以參考與相同的物件 `"c.d"` 。 參考此屬性的方式需要 `"a.b"` 或 `"c.d"` 在範圍內。 這個相同物件的參考不是，只要該物件的記憶體有效，就可以參考該物件。

 您 `IDebugProperty2` 可以將介面視為具有名稱、類型和位址的值。 相反地 `IDebugReference2` ，您可以將視為類型和位址。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
