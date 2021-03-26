---
description: 此介面可讓會話 debug manager (SDM) 控制在埠上執行的程式和進程。
title: IDebugPortEx2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e26fec4b47a301bfb266f40b41fd88216ccf671f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072425"
---
# <a name="idebugportex2"></a>IDebugPortEx2
此介面可讓會話 debug manager (SDM) 控制在埠上執行的程式和進程。

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂埠供應商會在執行 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)的相同物件上，執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 SDM 會呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugPort2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPortEx2` 。

|方法|描述|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|啟動可執行檔。|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|繼續執行進程。|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|判斷是否可以終止進程。|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|終止進程。|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|取得埠本身的處理序識別碼。|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|取得與程式節點相關聯的程式。|

## <a name="remarks"></a>備註
 這個介面通常在 SDM 和自訂埠供應商之間是私用的。

 如果需要，debug engine (DE) 可以在傳遞至[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)的[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面上尋找這個介面，然後使用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)來啟動程式。 但是，這並不是一項需求，而 DE 可以做任何需要執行的動作來啟動要求程式。

## <a name="requirements"></a>規格需求
 標頭： portpriv。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
