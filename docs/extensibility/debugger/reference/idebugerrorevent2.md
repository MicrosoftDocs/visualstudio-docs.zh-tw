---
description: 此介面會指定要向使用者回報的錯誤訊息。
title: IDebugErrorEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d531180ca2fad9a6605837105c4ec5d626584a19
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054227"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
此介面會指定要向使用者回報的錯誤訊息。

## <a name="syntax"></a>Syntax

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，將錯誤報表為人們看得懂的訊息。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 DE 會建立並傳送此事件物件來報告錯誤。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|`GetErrorMessage`|以人們可讀取的字串形式傳回錯誤。|

## <a name="remarks"></a>備註
 如果偵錯工具引擎遇到錯誤，則可以使用此介面透過 Visual Studio 向使用者報告訊息。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
