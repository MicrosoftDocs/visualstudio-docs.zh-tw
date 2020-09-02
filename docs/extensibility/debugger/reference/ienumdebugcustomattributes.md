---
title: IEnumDebugCustomAttributes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f8b521432124267d3f0e179d3a889fb599fa99d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717137"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
列舉自訂屬性。

## <a name="syntax"></a>語法

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會執行這個介面，以支援透過 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 介面 (的自訂屬性) 。

## <a name="notes-for-callers"></a>呼叫者注意事項
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 會傳回這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugCustomAttributes` 。

|方法|描述|
|------------|-----------------|
|[下一個](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|抓取列舉序列中指定數目的自訂屬性。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|略過列舉序列中指定數目的自訂屬性。|
|[重設](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|取得列舉值中的自訂屬性數目。|

## <a name="requirements"></a>需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
