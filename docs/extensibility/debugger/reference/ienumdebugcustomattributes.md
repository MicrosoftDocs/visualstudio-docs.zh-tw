---
title: IEnum調試自定義屬性 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717137"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
枚舉自定義屬性。

## <a name="syntax"></a>語法

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式實現此介面以支援自定義屬性(透過[IDebugCustom屬性](../../../extensibility/debugger/reference/idebugcustomattribute.md)介面)。

## <a name="notes-for-callers"></a>通話備註
- [枚舉自定義屬性](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugCustomAttributes`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|檢索枚舉序列中指定數量的自定義屬性。|
|[跳](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|在枚舉序列中跳過指定數量的自定義屬性。|
|[重設](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|獲取枚舉器中的自定義屬性數。|

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
