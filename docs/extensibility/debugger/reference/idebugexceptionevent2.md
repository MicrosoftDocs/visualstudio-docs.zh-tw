---
title: IDebugexception2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729787"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
除錯引擎 (DE) 在目前正在執行的程式中引發異常時,將此介面發送到工作階段調試管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面以報告正在調試的程式中發生了異常。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以報告異常。 該事件使用 SDM 在連接到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugExceptionEvent2`。

|方法|描述|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|獲取有關觸發此事件的異常的詳細資訊。|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|獲取引發此事件的異常的人類可讀描述。|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|確定除錯引擎 (DE) 是否支援在復原執行時將此異常傳遞給正在除錯的程式的選項。|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|指定是否應將異常傳遞到執行恢復時正在調試的程式,還是應丟棄該異常。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="remarks"></a>備註
 在發送事件之前,DE 會檢查此異常事件是否已被以前調用[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)指定為第一次或第二次異常。 如果已將其指定為第一次異常,則事件`IDebugExceptionEvent2`將發送到 SDM。 如果沒有,DE 會給應用程式處理異常的機會。 如果未提供異常處理程式,並且該異常已指定為第二個異常,則事件`IDebugExceptionEvent2`將發送到 SDM。 否則,DE 將恢復執行程式,作業系統或運行時處理異常。

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
