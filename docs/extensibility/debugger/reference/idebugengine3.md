---
description: 表示單一的 debug engine (DE) ，可控制一或多個模組的偵錯工具。
title: IDebugEngine3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a10f439ba344b71cd31fd990928b7804b6c11d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066185"
---
# <a name="idebugengine3"></a>IDebugEngine3
表示單一的 debug engine (DE) ，可控制一或多個模組的偵錯工具。

## <a name="syntax"></a>Syntax

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面是由自訂的 DE (（如果它支援符號) 來啟用 JustMyCode 狀態）所執行。 如果這個介面支援符號和 JustMyCode，則必須由 DE 來執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 會話 debug manager (SDM) 呼叫這個介面，以針對要載入符號的位置傳遞使用者選項。 當引擎具現化時，也會呼叫它來設定引擎的 GUID (此 GUID 是根據引擎註冊時的計量所產生的) 。 SDM 也會呼叫此介面來設定 JustMyCode 狀態，並將偵錯工具已知的所有例外狀況設定為指定的狀態。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)的方法之外，介面也會 `IDebugEngine3` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|設定 DE 將用來搜尋偵錯工具符號的路徑或路徑。|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|載入尚未載入其符號的所有模組的符號。|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|告知 JustMyCode 資訊。|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|從計量設定取消 GUID。|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|將目前未完成的所有例外狀況設定為指定的狀態。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
