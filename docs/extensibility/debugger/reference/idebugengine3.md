---
title: IDebugEngine3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730649"
---
# <a name="idebugengine3"></a>IDebugEngine3
表示控制一個或多個模組調試的單個調試引擎 (DE)。

## <a name="syntax"></a>語法

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由自定義 DE 實現(如果它支援符號)以啟用 JustMyCode 狀態。 如果 DE 支援符號和 JustMyCode,則必須實現此介面。

## <a name="notes-for-callers"></a>通話備註
 工作階段除錯管理員 (SDM) 呼叫此介面,以傳遞載入符號的位置的使用者選項。 在實例化引擎時,還調用它來設置引擎的 GUID(此 GUID 基於發動機註冊時的指標)。 SDM 還會調用此介面以設置 JustMyCode 狀態,並將調試器已知的所有異常設置為指定狀態。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)繼承的方法`IDebugEngine3`外, 介面還公開了以下方法。

|方法|描述|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|設置 DE 將用於搜索調試符號的路徑。|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|載入尚未載入其符號的所有模組的符號。|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|向 DE 提供有關 JustMyCode 資訊的資訊。|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|從指標設置 DE GUID。|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|將當前未完成的所有異常設置為指定狀態。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
