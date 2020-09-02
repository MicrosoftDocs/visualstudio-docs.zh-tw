---
title: IEnumDebugErrorBreakpoints2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716879"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
這個介面會列舉與暫止中斷點相關聯的錯誤中斷點。

## <a name="syntax"></a>語法

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 在它支援中斷點的過程中，執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 Visual Studio 會呼叫 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 來取得這個介面，此介面代表無法系結的中斷點清單，或 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) 來取得這個介面，代表未系結的中斷點清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugErrorBreakpoints2` 。

|方法|描述|
|------------|-----------------|
|[下一個](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|抓取列舉順序中指定的錯誤中斷點數目。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|略過列舉序列中指定的錯誤中斷點數目。|
|[重設](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|取得列舉值中的錯誤中斷點數目。|

## <a name="remarks"></a>備註
 此介面會保存 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 介面的清單，每個介面都會描述無法系結的中斷點，以及無法系結的原因。 Visual Studio 會使用 `IEnumDebugErrorBreakpoint2` 介面來更新 IDE 中顯示的中斷點。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
