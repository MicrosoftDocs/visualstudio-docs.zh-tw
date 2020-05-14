---
title: IDebug攔截異常完成事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a07f2808c1aaeca3c1631fce658fdf6e8da32d60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727760"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
當 DE 完成對被攔截事件的處理時,此介面由調試引擎 (DE) 發送到作業階段調試管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以報告已完成對截獲異常的處理。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以報告截獲異常的完成情況。 該事件使用 SDM 在連接到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 介面`IDebugInterceptExceptionCompleteEvent2`實現以下方法。

|方法|描述|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|返回與已處理的異常關聯的唯一值。|

## <a name="remarks"></a>備註
 當該方法成功完成處理被截獲的異常時,此事件將由[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)發送。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
