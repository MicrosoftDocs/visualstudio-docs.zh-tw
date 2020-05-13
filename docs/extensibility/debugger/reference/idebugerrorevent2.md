---
title: IDebugErrorevent2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00fd8b4b42f11d18958f8a969bc4ccd58754ab93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730008"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
此介面指定要向使用者報告的錯誤訊息。

## <a name="syntax"></a>語法

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面,將錯誤報告為人可讀訊息。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM 使用[查詢介面](/cpp/atl/queryinterface)訪問`IDebugEvent2`介面。

## <a name="notes-for-callers"></a>通話備註
 DE 創建並發送此事件物件以報告錯誤。 該事件使用 SDM 在連接到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 此介面實現以下方法:

|方法|描述|
|------------|-----------------|
|`GetErrorMessage`|將錯誤作為人可讀字串返回。|

## <a name="remarks"></a>備註
 如果調試引擎遇到錯誤,它可以使用此介面通過 Visual Studio 向用戶報告消息。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
