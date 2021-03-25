---
description: 視需要為此偵錯工具所進行的所有模組) 符號載入 (。
title: IDebugEngine3：： LoadSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43651baac29b3904b9bc12d8d4b965ca1cd8e3ee
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066174"
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
