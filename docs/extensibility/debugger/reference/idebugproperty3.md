---
title: IDebug屬性3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721050"
---
# <a name="idebugproperty3"></a>IDebugProperty3
此介面支援:

- 檢索與該屬性關聯的任意長字串。

- 將唯一 ID 與 屬性關聯。

- 檢索屬性的自定義檢視器清單。

- 設定屬性的值,並能夠回報任何產生的錯誤

## <a name="syntax"></a>語法

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 在實現[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)的同一物件上實現此介面,以支援長字串、屬性 IT 和自訂檢視器。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugProperty2`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從`IDebugProperty2`繼承的方法外`IDebugProperty3`, 介面還公開以下方法。

|方法|描述|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|返回與屬性關聯的字串的長度。|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|返回使用者提供的緩衝區中的字串。|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|為此屬性創建唯一 ID。|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|銷毀此屬性的唯一 ID。|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|返回可以使用此屬性查看的自定義查看器數。|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|返回可以使用此屬性查看的自定義查看器的清單。|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|設定此屬性的值,如果出現問題,將返回錯誤消息。|

## <a name="remarks"></a>備註
- [SetValueAsString WithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)是工作階段除錯管理員 (SDM) 設定屬性值的首選方式。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
