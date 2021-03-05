---
description: 視需要為此偵錯工具所進行的所有模組) 符號載入 (。
title: IDebugEngine3：： LoadSymbols |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4b4f210ef07ad10b35251582dd8a3c0fe3b0685
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153803"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
視需要為此偵錯工具所進行的所有模組) 符號載入 (。

## <a name="syntax"></a>語法

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這會為此偵錯工具引擎所參考的所有模組載入偵錯工具符號。 只有當符號尚未載入時，才會載入這些符號。 符號會在呼叫 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)所設定的路徑上搜尋。

## <a name="see-also"></a>另請參閱
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
