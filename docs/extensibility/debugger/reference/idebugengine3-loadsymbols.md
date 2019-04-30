---
title: IDebugEngine3::LoadSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff317b217b72fcb5a6042747abd88e5a9d344f7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875358"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
正在偵錯此偵錯引擎的所有模組的載入 （視） 符號。

## <a name="syntax"></a>語法

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

#### <a name="parameters"></a>參數
 無。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這會載入此偵錯引擎所參考的所有模組的偵錯符號。 他們尚未載入時，才會載入的符號。 呼叫所設定的路徑上搜尋符號[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)。

## <a name="see-also"></a>另請參閱
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)